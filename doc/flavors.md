```text
SPDX-License-Identifier: Apache-2.0
Copyright (c) 2020 Intel Corporation
```
<!-- omit in toc -->
# OpenNESS Deployment Flavors
This document introduces the supported deployment flavors that are deployable through the OpenNESS Experience Kits (OEK).
- [Minimal Flavor](#minimal-flavor)
- [FlexRAN Flavor](#flexran-flavor)
- [Media Analytics Flavor](#media-analytics-flavor)
- [Media Analytics Flavor with VCAC-A](#media-analytics-flavor-with-vcac-a)
- [CDN Transcode Flavor](#cdn-transcode-flavor)
- [CDN Caching Flavor](#cdn-caching-flavor)

## Minimal Flavor
The pre-defined *minimal* deployment flavor provisions the minimal set of configurations for bringing up the OpenNESS network edge deployment.

Steps to install this flavor are as follows:
1. Configure OEK as described in the [OpenNESS Getting Started Guide for Network Edge](getting-started/network-edge/controller-edge-node-setup.md).
2. Run OEK deployment script:
    ```shell
    $ deploy_ne.sh -f minimal
    ```

This deployment flavor enables the following ingredients:
* Node Feature Discovery
* The default Kubernetes CNI: `kube-ovn`
* Telemetry

## FlexRAN Flavor 
The pre-defined *flexran* deployment flavor provisions an optimized system configuration for vRAN workloads on Intel Xeon servers. It also provisions for deployment of PACN3000 FPGA tools and components enabling the offload of acceleration of FEC (Forward Error Correction) to the FPGA.

Steps to install this flavor are as follows:
1. Configure OEK as described in the [OpenNESS Getting Started Guide for Network Edge](getting-started/network-edge/controller-edge-node-setup.md).
2. Run OEK deployment script:
    ```shell
    $ deploy_ne.sh -f flexran
    ```
This deployment flavor enables the following ingredients:
* Node Feature Discovery
* SRIOV device plugin with FPGA configuration
* Calico CNI
* Telemetry
* FPGA remote system update through OPAE
* FPGA configuration
* RT Kernel
* Tapology Manager
* RMD operator
  
## Media Analytics Flavor
The pre-defined *media-analytics* deployment flavor provisions an optimized system configuration for media analytics workloads on Intel Xeon servers. It also provisions a set of video analytics services based on the [Video Analytics Serving](https://github.com/intel/video-analytics-serving) for analytics pipeline management and execution.

Steps to install this flavor are as follows:
1. Configure OEK as described in the [OpenNESS Getting Started Guide for Network Edge](getting-started/network-edge/controller-edge-node-setup.md).
2. Run OEK deployment script:
    ```shell
    $ deploy_ne.sh -f media-analytics
    ```

This deployment flavor enables the following ingredients:
* Node Feature Discovery
* VPU & GPU device plugins
* HDDL daemonset
* The default Kubernetes CNI: `kube-ovn`
* Video analytics services
* Telemetry

## Media Analytics Flavor with VCAC-A
The pre-defined *media-analytics-vca* deployment flavor provisions an optimized system configuration for media analytics workloads leveraging VCAC-A acceleration. It also provisions a set of video analytics services based on the [Video Analytics Serving](https://github.com/intel/video-analytics-serving) for analytics pipeline management and execution.

Steps to install this flavor are as follows:
1. Configure OEK as described in the [OpenNESS Getting Started Guide for Network Edge](getting-started/network-edge/controller-edge-node-setup.md).
2. Add the VCA host name in the [edgenode_vca_group] group in `inventory.ini` file of the OEK, e.g:
    ```
    [edgenode_vca_group]
    silpixa00400194
    ```
3. Run OEK deployment script:
    ```shell
    $ deploy_ne.sh -f media-analytics-vca
    ```

> **NOTE:** At the time of writing this document, *Weave Net* is the only supported CNI for network edge deployments involving VCAC-A acceleration. The `weavenet` CNI is automatically selected by the *media-analytics-vca*.

This deployment flavor enables the following ingredients:
* Node Feature Discovery
* VPU & GPU device plugins
* HDDL daemonset
* The `weavenet` Kubernetes CNI
* Video analytics services
* Telemetry

## CDN Transcode Flavor
The pre-defined *cdn-transcode* deployment flavor provisions an optimized system configuration for cdn transcode sample workloads on Intel Xeon servers. 

Steps to install this flavor are as follows:
1. Configure OEK as described in the [OpenNESS Getting Started Guide for Network Edge](getting-started/network-edge/controller-edge-node-setup.md).
2. Run OEK deployment script:
    ```shell
    $ deploy_ne.sh -f cdn-transcode
    ```

This deployment flavor enables the following ingredients:
* Node Feature Discovery
* The default Kubernetes CNI: `kube-ovn`
* Telemetry

## CDN Caching Flavor
The pre-defined *cdn-caching* deployment flavor provisions an optimized system configuration for cdn content delivery workloads on Intel Xeon servers. 

Steps to install this flavor are as follows:
1. Configure OEK as described in the [OpenNESS Getting Started Guide for Network Edge](getting-started/network-edge/controller-edge-node-setup.md).
2. Run OEK deployment script:
    ```shell
    $ deploy_ne.sh -f cdn-caching
    ```

This deployment flavor enables the following ingredients:
* Node Feature Discovery
* The `kube-ovn` and `sriov` Kubernetes CNI
* Telemetry
* Kubernetes Topology Manager policy: `single-numa-node`
