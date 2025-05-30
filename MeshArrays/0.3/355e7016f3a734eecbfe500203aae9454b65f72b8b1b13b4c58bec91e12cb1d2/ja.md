```
varmeta
```

varmeta データ構造。デフォルトでは、`unit` は `missing`（無次元）、`position` は `fill(0.5,3)`（セルの中心）、時間は `missing`、および `name` / `long_name` は `unknown` です。

利用可能なコンストラクタ：

```
varmeta(unit::Union{Unitful.Units,Number,Missing},position::Array{Float64,1},
        time::Union{DateTime,Missing,Array{DateTime,1}},name::String,long_name::String)
```

および：

`defaultmeta = varmeta(missing,fill(0.5,3),missing,"unknown","unknown")`
