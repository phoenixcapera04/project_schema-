FROM rocker/shiny:latest

RUN apt-get update && apt-get install -y \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    libpq-dev

RUN R -e "install.packages(c('shiny', 'tidyverse', 'plotly', 'DT', 'shinydashboard', 'readr'), repos='https://cloud.r-project.org')"

WORKDIR /srv/shiny-server/
COPY shiny_app/ .

EXPOSE 3838
CMD ["R", "-e", "shiny::runApp('/srv/shiny-server', host='0.0.0.0', port=3838)"]
