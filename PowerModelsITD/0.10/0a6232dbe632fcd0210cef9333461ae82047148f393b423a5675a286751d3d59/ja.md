```
function make_lossless!(
    pmitd_data::Dict{String,<:Any}
)
```

対応する変換を適用して、ロスモデルを持つオブジェクトからパラメータを削除し、ロスレスにします。これには、すべてのロスモデルパラメータを省略できるスイッチ、電圧源、変圧器が含まれます。
