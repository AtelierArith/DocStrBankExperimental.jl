```
modify_model!(mod::DCLine, config, data, model)
```

Add dc lines to the model from `data[:dc_lines]`, creating `pflow_dc` variables, and adding/subtracting to the corresponding `pflow_bus` variables.
