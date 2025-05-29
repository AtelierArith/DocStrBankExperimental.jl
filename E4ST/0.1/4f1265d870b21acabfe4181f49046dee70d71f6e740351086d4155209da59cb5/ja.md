```
function E4ST.modify_model!(pol::PTC, config, data, model)
```

その年のPTC価格 * 発電量を目的関数から引き算します [`add_obj_term!(data, model, PerMWhGen(), pol.name, oper = -)`](@ref) を使用して
