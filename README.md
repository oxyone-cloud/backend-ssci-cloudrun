<p align="center">
  <img width="640" alt="OxyONE SSCI Cloud Backend" src="https://github.com/user-attachments/assets/6f0e8536-5dff-4e29-a55c-fd968adb0e21" />
</p>

<p align="center">
  <a href="https://orcid.org/0009-0000-1250-8205">
    <img src="https://img.shields.io/badge/ORCID-0009--0000--1250--8205-A6CE39?style=flat&logo=orcid&logoColor=white" alt="ORCID"/>
  </a>
  <img src="https://img.shields.io/badge/Startup_Labellisée-Algérie-blue?style=flat&logo=rocket&logoColor=white" alt="Startup Labellisée"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-%2343853D.svg?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js"/>
  <img src="https://img.shields.io/badge/Render-%2346E3B7.svg?style=for-the-badge&logo=render&logoColor=white" alt="Render"/>
  <img src="https://img.shields.io/badge/GoogleCloud-%234285F4.svg?style=for-the-badge&logo=google-cloud&logoColor=white" alt="Google Cloud Datastore"/>
</p>

# 🧊 OxyONE / SSCI Cloud Backend (`backend-ssci-cloudrun`)

Backend Node.js / Express déployé sur Render pour la collecte, le traitement et la gestion des données de capteurs IoT de la chaîne du froid.
<a href="https://www.codehype.ai/product/oxyone?utm_source=codehype_badge" target="_blank" rel="noopener noreferrer">
  <img src="https://www.codehype.ai/badges/oxyone.svg?variant=find-us&v=20" alt="Featured on CodeHype" width="180" height="65" loading="lazy" decoding="async" style="display:inline-block;border:0;width:100%;max-width:180px;height:auto;max-height:65px;" />
</a>

---

## 📐 Architecture du Système

```mermaid
graph TD
    subgraph CLIENTS ["📱 Clients & Sources de Données"]
        App["Application Mobile / IoT"]
        Web["Navigateur Web"]
    end

    subgraph RENDER ["🚀 Render Web Service"]
        Express["Serveur Express (Port 10000)"]
        Root["GET / (Healthcheck)"]
        AddData["POST /addData (Sensors)"]
    end

    subgraph GCP ["☁️ Google Cloud Platform"]
        Datastore[("Datastore (SensorData)")]
    end

    App -->|HTTPS POST| AddData
    Web -->|HTTPS GET| Root
    AddData -->|Save Entity| Datastore
