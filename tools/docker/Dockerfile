FROM ubuntu:18.04
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update -y && apt-get install -y python3 python3-dev \
    git pandoc wget python3-pip texlive-xetex

# ^tex-live is a big one. The missing executable was 'xelatex':

RUN pip3 install --upgrade pip
# need file for pandas chapter

# Install nbconvert (because of this issue
# https://github.com/jupyter/nbconvert/issues/1223)
# nbconvert 6.0 is not released yet (as of Sept 2020)
RUN pip3 install git+https://github.com/jupyter/nbconvert.git@6.0.0b7
# Remove the above, once nbconvert6 is released

# install the remainder from requirements file
ADD requirements.txt requirements.txt
RUN pip3 install -r requirements.txt
RUN mkdir -p /io
WORKDIR /io
CMD ["/bin/bash"]
