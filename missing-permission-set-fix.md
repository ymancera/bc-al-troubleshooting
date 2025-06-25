# Guía de Solución de Problemas - Business Central AL

## Error: "Table is missing a matching permission set"

### Problema
Al compilar una tabla en Business Central AL aparece el error:
```
Table XXXXX 'Table Name' is missing a matching permission set.
```

### Solución Rápida

1. **Abrir la Paleta de Comandos**
   - Presiona `Ctrl + Shift + P` (Windows) o `Cmd + Shift + P` (Mac)

2. **Ejecutar el Comando**
   - Busca y ejecuta: `AL: Generate Permission Set`
   - O escribe: `Generate Permission Set`

3. **Resultado**
   - Se creará automáticamente un archivo `.permissionset.al` en tu proyecto
   - El archivo contendrá los permisos necesarios para todos los objetos

### Qué hace este comando

- Escanea todos los objetos AL en tu proyecto (tablas, páginas, codeunits, etc.)
- Genera automáticamente un permission set con los permisos mínimos requeridos
- Crea el archivo con la nomenclatura correcta

### Archivo generado típico
```al
permissionset 50000 "My Permission Set"
{
    Assignable = true;
    Permissions = 
        table "My Table" = X,
        page "My Page" = X;
}
```

### Notas Importantes
- ✅ Ejecuta este comando cada vez que agregues nuevos objetos
- ✅ El comando respeta los rangos de IDs definidos en tu `app.json`
- ✅ Es seguro ejecutarlo múltiples veces (actualiza el archivo existente)

---
*By Yeins*
