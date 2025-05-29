```
instantiate_model(
    data::Dict{String,<:Any},
    model_type::Type,
    build_method::Function;
    kwargs...)::AbstractWaterModel
```

入力ファイルから `file` のファイルパスを持つ WaterModels オブジェクトをインスタンス化して返します。ここで、`model_type` は定式化タイプ（例：NCWaterModel）であり、`build_method` は考慮されている問題仕様を構築するための関数です（例：build*mn*owf）。
