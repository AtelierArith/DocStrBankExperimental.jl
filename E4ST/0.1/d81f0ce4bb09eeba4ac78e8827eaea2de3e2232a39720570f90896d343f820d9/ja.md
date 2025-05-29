```
function E4ST.modify_model!(pol::ITC, config, data, model)
```

その年のITC価格 * キャパシティを目的関数から引き算します [`add_obj_term!(data, model, PerMWCap(), pol.name, oper = -)`](@ref) を使用して
