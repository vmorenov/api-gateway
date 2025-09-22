# 🚀 API Gateway - Spring Cloud Gateway (WebFlux)

[![Java](https://img.shields.io/badge/Java-21-blue)](https://openjdk.org/projects/jdk/21/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.1.8-brightgreen)](https://spring.io/projects/spring-boot)
[![Spring Cloud](https://img.shields.io/badge/Spring%20Cloud-2023.0.3-important)](https://spring.io/projects/spring-cloud)
[![Security](https://img.shields.io/badge/Spring%20Security-OAuth2%20JWT-yellow)](https://spring.io/projects/spring-security)

---

## 📌 Descripción

Este proyecto implementa un **API Gateway** basado en **Spring Cloud Gateway (WebFlux)** que actúa como punto único de entrada para los microservicios.  

Incluye validación de **tokens JWT OAuth2** emitidos por un Authorization Server (Spring Authorization Server), con soporte para integración futura de **Google reCAPTCHA v3** en rutas críticas (ejemplo: envío de correos).  

### ✨ Funcionalidades principales
- Enrutamiento dinámico de peticiones HTTP hacia microservicios.
- Validación de **OAuth2 JWT** mediante `spring-boot-starter-oauth2-resource-server`.
- Configuración de **rutas críticas** con posibilidad de filtros adicionales (ej. reCAPTCHA).
- Configuración CORS global.
- Logging de peticiones y soporte ANSI color para mejor lectura en consola.

---

## 🏗️ Arquitectura

```mermaid
flowchart LR
    A[Frontend / Cliente] -->|Bearer JWT + Headers| B[API Gateway]
    B -->|Valida JWT contra Authorization Server| C[Security Server]
    B -->|Ruta crítica con X-Recaptcha-Token| D[Recaptcha Service]
    B -->|Rutas válidas| E[Microservicios: Email, Productos, Notificación, etc.]
