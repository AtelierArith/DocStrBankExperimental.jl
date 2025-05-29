```
function E4ST.modify_model!(pol::ITCStorage, config, data, model)
```

その年のITCStorageの価格 * 容量を目的関数から引き算します [`add_obj_term!(data, model, PerMWCap(), pol.name, oper = -)`](@ref) を使用して
