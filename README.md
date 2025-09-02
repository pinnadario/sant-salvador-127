# SANT SALVADOR 127 - Sistema de Gestión de Gastos v3.0

Sistema web para gestionar inquilinos, gastos y pagos de un piso compartido con integración a GitHub.

## Características

- **Gestión de inquilinos** con fechas de entrada y salida
- **Registro de gastos** por categorías (agua, luz, gas, internet, otros)  
- **Control de pagos** y adelantos de inquilinos
- **Cálculo automático de balances** proporcionales
- **Integración con GitHub** para almacenamiento de datos
- **Backup local** en localStorage del navegador
- **Exportación a CSV** para análisis externos

## Estructura del Repositorio

```
sant-salvador-127/
├── index.html          # Sistema principal
├── data/
│   ├── inquilinos.json  # Datos de inquilinos
│   ├── gastos.json      # Registro de gastos
│   ├── pagos.json       # Registro de pagos
│   └── config.json      # Configuración del sistema
└── README.md           # Este archivo
```

## Configuración

### 1. Usar el sistema
1. Abre `index.html` en tu navegador
2. Ve a la sección "5.DATOS"
3. Introduce: `pinnadario/sant-salvador-127`
4. Haz clic en "CONFIGURAR"
5. Haz clic en "CARGAR" para sincronizar

### 2. GitHub Pages (opcional)
- Ve a Settings → Pages
- Selecciona "Deploy from a branch: main"
- Sistema disponible en: `https://pinnadario.github.io/sant-salvador-127`

## Uso del Sistema

### INQUILINOS
- Añadir nuevos inquilinos con fechas de check-in/out
- Ver historial de inquilinos activos y pasados

### GASTOS
- Registrar facturas de servicios (agua, luz, gas)
- Gastos anuales proporcionales (seguro, escalera)
- Gastos mensuales fijos (internet)

### PAGOS
- Registrar adelantos de inquilinos
- Asociar pagos a inquilinos específicos

### BALANCES
- Calcular lo que debe cada inquilino por período
- Reparto automático 50/50 de gastos
- Estimación de períodos sin facturas

## Lógica de Cálculos

1. **Gastos con período específico** (agua, luz, gas): Proporcional según días de solapamiento
2. **Gastos mensuales fijos** (internet): Mes completo si estuvo cualquier día
3. **Gastos anuales** (seguro, escalera): Proporcional según días totales
4. **Reparto**: Cada inquilino paga el 50% de los gastos del período
5. **Estimaciones**: Para períodos sin facturas, se estima basándose en facturas adyacentes

## Actualizar Datos

### Para modificar datos:
1. Edita los archivos JSON directamente en GitHub
2. En el sistema web, haz clic en "CARGAR" para sincronizar

### Formato de datos:

**inquilinos.json**
```json
[
  {
    "id": 1001,
    "nombre": "NOMBRE DEL INQUILINO",
    "checkin": "2025-01-01",
    "checkout": "2025-07-31"
  }
]
```

**gastos.json**
```json
[
  {
    "id": 3001,
    "tipo": "AGUA",
    "descripcion": "AGUA 10/01/2025 - 21/03/2025 #20251946789",
    "importe": 69.83,
    "fecha": "2025-01-10"
  }
]
```

**pagos.json**
```json
[
  {
    "id": 4001,
    "inquilinoId": 1001,
    "nombre": "SERGIO Y ANA",
    "importe": 75,
    "fecha": "01/02/2025"
  }
]
```

## Compatibilidad

- Chrome, Firefox, Safari, Edge modernos
- Móvil y desktop
- Funciona offline (usando datos locales)
- No requiere servidor ni base de datos

## URLs de archivos

- https://raw.githubusercontent.com/pinnadario/sant-salvador-127/main/data/inquilinos.json
- https://raw.githubusercontent.com/pinnadario/sant-salvador-127/main/data/gastos.json
- https://raw.githubusercontent.com/pinnadario/sant-salvador-127/main/data/pagos.json
- https://raw.githubusercontent.com/pinnadario/sant-salvador-127/main/data/config.json

## Solución de Problemas

**Error cargando desde GitHub:**
- Verifica que el repositorio sea público
- Los archivos JSON deben estar en `data/` (no en `data/data/`)
- GitHub puede tardar unos minutos en actualizar archivos

**Cálculos incorrectos:**
- Revisa formato de fechas: `dd/mm/yyyy - dd/mm/yyyy`
- Períodos de facturas deben seguir el formato correcto

---

Sistema creado para SANT SALVADOR 127
