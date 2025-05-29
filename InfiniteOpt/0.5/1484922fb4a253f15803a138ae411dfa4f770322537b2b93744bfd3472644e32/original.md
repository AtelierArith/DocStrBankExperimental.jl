```
add_registered_to_jump(opt_model::JuMP.Model, inf_model::InfiniteModel)::Nothing
```

Add the user registered functions in `inf_model` to a `JuMP` model `opt_model`.  This is intended as an internal method, but it is provided for developers that  extend `InfiniteOpt` to use other optimizer models.
