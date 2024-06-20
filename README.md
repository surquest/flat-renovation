# Introduction

This repository holds all the information relavant to the flat reconstruction at the place where I am living.

# Project structure

This project follows structure as outlined below:

```bash
├── docs                                      # project documentation for MKDocs published in GitLab Pages          
├── docs.dockerfile                      # base docker image for the documentation
├── docs.requirements.txt                     # requirements specification for the MkDocs documentation 
└── README.md                                 # this file ;o)
```

# Documentation

Complete documentation can be found on [GitHub Pages](http://analytics.docs.wearerealitygames.com/analytical-data-mart/etl/binance/). The documentation can be also created locally with help of MkDocs in docker.

```powershell
    # NOTE: These commands are in powershell syntax
    
    # creation of the docker image from the Dockerfile
    docker build -t docs/mkdocs-material -f docs.base.dockerfile .
    
    # Serve the documentation locally
    docker run --rm -it `
     --name mkdocs `
     -v ${PWD}:/opt/project `
     -p 8000:8000 `
     docs/mkdocs-material mkdocs serve --dev-addr 0.0.0.0:8000
    
    # Build the documentation as static pages
    docker run --rm -it `
     --name mkdocs-build `
     -v ${PWD}:/opt/project `
     docs/mkdocs-material mkdocs build --strict --verbose --site-dir dist
```