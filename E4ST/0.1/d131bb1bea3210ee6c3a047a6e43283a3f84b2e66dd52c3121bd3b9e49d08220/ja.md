```
function add_obj_exp!(data, model, term::Term, s::Symbol; oper)
```

式 s（モデル内で既に定義されている）を目的関数 model[:obj] に追加します。名前、oper、および項のタイプを data[:obj_vars] に追加します。
