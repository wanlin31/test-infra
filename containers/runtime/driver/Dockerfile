# Copyright 2020 gRPC authors
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM debian:buster

RUN mkdir -p /src/workspace
WORKDIR /src/workspace

RUN apt-get update && apt-get install -y \
  autoconf \
  build-essential \
  clang \
  curl \
  git \
  make \
  libtool \
  libgflags-dev \
  pkg-config \
  gnupg \
  apt-transport-https \
  ca-certificates \
  python3-dev \
  python3-pip \
  python3-setuptools \
  python3-yaml && \
  apt-get clean

RUN echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] http://packages.cloud.google.com/apt cloud-sdk main" | \
  tee -a /etc/apt/sources.list.d/google-cloud-sdk.list && curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | \
  apt-key --keyring /usr/share/keyrings/cloud.google.gpg  add - && apt-get update -y && apt-get install google-cloud-sdk -y && \
  apt-get clean

RUN pip3 install \
  protobuf \
  google-api-python-client \
  oauth2client \
  google-auth-oauthlib \
  tabulate \
  six==1.10.0 \
  pyasn1_modules==0.2.2 \
  pyasn1==0.4.2

CMD ["bash"]
