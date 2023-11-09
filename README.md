# Introduction
All of Helm chart to deploy ELK Stack services (Elasticsearch, Logstash, Kibana, and Filebeat).

# Prerequisites
1. Helm ([Helm docs](https://helm.sh/docs/intro/install/))
2. Accessible domain (preferred TLD) to expose Kibana service to internet
3. Update deployment config as your infra needs (replicas, ingress, resources, etc)

# Deployment Step by Step
In the root directory, run all of the following commands:

## 1. Create new namespace
You can name it whatever you like. In this example we create the name `elk`.

This namespace will be used when installing each services (see parameter `-n`).
```bash
kubectl create namespace elk
```

## 2. Install `Logstash` (log aggregator)
```bash
helm install -n elk logstash ./logstash
```

## 3. Install `Filebeat` (log agent)
```bash
helm install -n elk filebeat ./filebeat
```

## 4. Install `Elasticsearch` (log database)
```bash
helm install -n elk elasticsearch ./elasticsearch
```

## 5. Install `Kibana` (log dashboard/data visualizer)
```bash
helm install -n elk kibana ./kibana
```