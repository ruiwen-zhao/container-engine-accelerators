# Copyright 2021 Google Inc. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

TAG?=latest
REGISTRY?=gcr.io/google-containers
IMAGE=ubuntu-nvidia-driver-installer

container:
	docker build --build-arg base_image=ubuntu:16.04 --pull -t ${REGISTRY}/${IMAGE}:16.04-${TAG} -t ${REGISTRY}/${IMAGE}:${TAG} .
	docker build --build-arg base_image=ubuntu:18.04 --pull -t ${REGISTRY}/${IMAGE}:18.04-${TAG} .
	docker build --build-arg base_image=ubuntu:20.04 --pull -t ${REGISTRY}/${IMAGE}:20.04-${TAG} .

push:
	gcloud docker -- push ${REGISTRY}/${IMAGE}:${TAG}
	gcloud docker -- push ${REGISTRY}/${IMAGE}:16.04-${TAG}
	gcloud docker -- push ${REGISTRY}/${IMAGE}:18.04-${TAG}
	gcloud docker -- push ${REGISTRY}/${IMAGE}:20.04-${TAG}

.PHONY: container push
