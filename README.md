# Examen Práctico: Control de Sala

**Curso:** 4100901 - Estructuras Computacionales

**Condiciones:** Supervisado, con acceso al código fuente y a internet (sin uso de IA)

---

## ✅ Parte 2: Actividades Técnicas a Realizar (100 minutos)

### 1. Control automático de iluminación \[20%]

Al presionar el botón B1, la lámpara debe encenderse al 100%. Luego de 10 segundos, debe volver al brillo anterior configurado por UART.

Recomendaciones:

* Use `systick_get_tick()` para manejar los tiempos.
* Guarde el valor anterior del PWM para restaurarlo.

---

### 2. Activar bit de paridad UART \[10%]

Modifique la configuración de la UART para que se active el **bit de paridad impar (odd parity)**, de modo que el sistema sea más confiable en ambientes ruidosos como instalaciones industriales.

Recomendaciones:

* Consulte la documentación del registro `CR1` de USART2.
* Verifique que la comunicación serial con la terminal funcione correctamente con la nueva configuración.

---

### 3. Remapeo del pin PWM a PB4 \[10%]

Actualmente la lámpara usa PA6 para la salida PWM (TIM3\_CH1).

Reemplace esta configuración para usar **PB4** (que también puede usar TIM3\_CH1) como nuevo pin de salida PWM.

Recomendaciones:

* Verifique el AF de PB4 en el manual de referencia.
* Actualice la configuración en `gpio.h`, `gpio.c`, y `tim.c`.

---

### 4. Mensaje de bienvenida \[10%]

Al iniciar el sistema, se debe imprimir vía UART:

```
Controlador de Sala v1.0
Desarrollador: [Nombre del estudiante]
Estado inicial:
 - Lámpara: 20%
 - Puerta: Cerrada
```

Debe colocarse en `room_control_app_init()`.

---

### 5. Comando UART para ver estado actual \[10%]

Implemente el comando `'s'` para que por UART se imprima:

```
Estado:
 - Lámpara: 70%
 - Puerta: Abierta
```

Este debe reflejar el estado real de las variables del sistema.

---

### 6. Comando de ayuda UART \[10%]

Implemente el comando `'?'` para que al enviarlo vía UART se muestre un resumen de uso del sistema. Ejemplo:

```
Comandos disponibles:
 '1'-'4': Ajustar brillo lámpara (100%, 70%, 50%, 20%)
 '0'   : Apagar lámpara
 'o'   : Abrir puerta
 'c'   : Cerrar puerta
 's'   : Estado del sistema
 '?'   : Ayuda
```

---

### 7. Transición gradual de brillo \[10%]

Implemente el comando `'g'` para hacer que la lámpara aumente gradualmente de 0% a 100% en pasos de 10% cada 500ms.

---
