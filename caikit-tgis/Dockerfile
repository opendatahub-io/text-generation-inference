FROM server-release as caitkit-tgis-server

ARG CAIKIT_NLP_REPO=https://github.com/caikit/caikit-nlp

# caikit-nlp has caikit and caikit-tgis-backend as dependencies
# In future this will be replaced with just standard pip installs
RUN yum -y install git && \
    git clone ${CAIKIT_NLP_REPO} && \
    pip install --no-cache-dir ./caikit-nlp && \
    mkdir -p /opt/models && \
    mkdir -p /caikit/config

# Copy config file template into place, this config
# covers enabling TGIS
COPY template.yml /caikit/config
# start-serving.sh 
COPY start-serving.sh /

ENV RUNTIME_LIBRARY='caikit_nlp' \
    RUNTIME_LOCAL_MODELS_DIR='/opt/models'

CMD [ "/start-serving.sh" ]