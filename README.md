# Orthanc DICOM Server Setup Guide

This document outlines the steps required to set up an Orthanc server using Docker, configure the environment, and send DICOM files from a remote system to the Orthanc server. Orthanc is an open-source, lightweight DICOM server ideal for medical imaging management.

## Table of Contents

1. [Setting Up Orthanc with Docker](#setting-up-orthanc-with-docker)
    - [Install Docker](#install-docker)
    - [Build the Docker Image for Orthanc](#build-the-docker-image-for-orthanc)
    - [Create a Custom Config for the Orthanc Server](#create-a-custom-config-for-the-orthanc-server)
    - [Create Docker Compose File](#create-docker-compose-file)
    - [Start the Orthanc Server](#start-the-orthanc-server)
2. [Sending DICOM Files to Orthanc Server](#sending-dicom-files-to-orthanc-server)
    - [Install DCMTK on the Sender’s Machine](#install-dcmtk-on-the-senders-machine)
    - [Send DICOM Files Using storescu](#send-dicom-files-using-storescu)
3. [Requirements and Permissions](#requirements-and-permissions)
    - [Network Connectivity](#network-connectivity)
    - [Orthanc Configuration](#orthanc-configuration)
    - [DICOM Files](#dicom-files)
    - [Privileges and Permissions](#privileges-and-permissions)
    - [Testing and Troubleshooting](#testing-and-troubleshooting)
4. [Remote Connection Options](#remote-connection-options)

## Setting Up Orthanc with Docker

### Install Docker

Ensure Docker is installed on your system. If not, you can install Docker by following the official installation guide for your operating system.

### Build the Docker Image for Orthanc

Install the necessary packages to build the Docker image for running the Orthanc server. Follow the instructions mentioned on the [Orthanc Builder GitHub repository](https://github.com/orthanc-server/orthanc-builder).

### Create a Custom Config for the Orthanc Server

1. Create a directory for your Orthanc setup and navigate into it.
2. Create a file `orthanc-config/orthanc.json` and set custom configurations, including the username and password for your Orthanc server.

```json
{
  "Name": "Orthanc-First",
  "RemoteAccessAllowed": true,
  "AuthenticationEnabled": true,
  "HttpServerEnabled": true,
  "RegisteredUsers": {
    "MyOrthancServer": "testing@123"
  },
  "DicomAet": "ORTHANC",
  "DicomPort": 4242,
  "HttpPort": 8042,
  "HttpVerbose": true,
  "DicomModalities": {},
  "OrthancPeers": {}
}
