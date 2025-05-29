```
@config default_config my_function(x; a, b) = ...
```

This macro creates a function `my_function(config, x)` which will have access to the variables `a` and `b`. The values `a` and `b` will be those in `config`, if they are present, or else those in `default_config`.
