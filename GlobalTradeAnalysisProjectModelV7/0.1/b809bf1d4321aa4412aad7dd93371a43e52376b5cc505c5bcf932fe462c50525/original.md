```
generate_calibration_inputs(model_container, start_data)
```

Produces the required inputs for default calibration. The calibration is focused on the value flows in the GTAP database.

### Args:

  * `model_container`: the model container with the current model
  * `start_data`: a dictionary with the data representing the desired calibration level

### Returns

A named tuple with two elements: `fixed_calibration` containing the closure, and `data_calibration` containing the desired calibration data. 
