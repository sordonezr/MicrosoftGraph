# Obtener reuniones de Teams a través de Microsoft Graph

## Endpoint

```bat
GET https://graph.microsoft.com/v1.0/me/calendarView
```
Este endpoint recupera la vista del calendario para el usuario autenticado dentro de un rango de tiempo especificado. Permite seleccionar propiedades específicas de los eventos del calendario y limitar el número de eventos devueltos.
## Parámetros
* startDateTime: La fecha y hora de inicio del rango, en formato UTC. (ejemplo: 2024-06-01T00:00:00Z)
* endDateTime: La fecha y hora de fin del rango, en formato UTC. (ejemplo: 2024-06-30T23:59:59Z)
* $select: Una lista de propiedades, separadas por comas, para incluir en la respuesta. En este ejemplo, las propiedades seleccionadas son subject, start y isOnlineMeeting.
* $top: El número máximo de elementos a devolver en la respuesta. En este ejemplo, está establecido en 500.
## Ejemplo de Solicitud
```bat
GET https://graph.microsoft.com/v1.0/me/calendarView?startDateTime=2024-06-01T00:00:00Z&endDateTime=2024-06-30T23:59:59Z&$select=subject,start,isOnlineMeeting&$top=500
```
## Ejemplo de respuesta

```json
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('user_id')/calendarView(subject,start,isOnlineMeeting)",
    "value": [
        {
            "subject": "Reunión con el equipo",
            "start": {
                "dateTime": "2024-06-01T09:00:00",
                "timeZone": "UTC"
            },
            "isOnlineMeeting": true
        },
        {
            "subject": "Llamada con el cliente",
            "start": {
                "dateTime": "2024-06-02T14:00:00",
                "timeZone": "UTC"
            },
            "isOnlineMeeting": false
        },
        ...
    ]
}

```

## Nota

* Asegúrese de tener los permisos apropiados para acceder al calendario del usuario. Los permisos requeridos pueden incluir Calendars.Read o Calendars.ReadWrite.
* Este endpoint soporta parámetros de consulta OData para ayudar a personalizar la respuesta.

## Uso

* Este endpoint puede ser utilizado para obtener eventos del calendario de un usuario dentro de un rango de tiempo específico, lo cual puede ser útil para crear horarios, recordatorios o integrar datos del calendario en otras aplicaciones.
