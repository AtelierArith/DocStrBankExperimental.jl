```
rebuild_model(mc; calibration = false)
```

Rebuilds the model, typically to create a slimmer model without calibration equations

### Args:

  * `mc`: model container
  * `calibration`: include calibration equations

## Returns:

An updated model container

### Example:

$julia rebuild_model!(mc)$
