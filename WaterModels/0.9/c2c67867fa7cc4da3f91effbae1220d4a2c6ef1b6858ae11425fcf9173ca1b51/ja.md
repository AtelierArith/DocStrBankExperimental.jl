```
instantiate_model(
    file::String,
    model_type::Type,
    build_method::Function;
    kwargs...)::AbstractWaterModel
```

データ辞書 `data` から WaterModels オブジェクトをインスタンス化して返します。ここで、`model_type` は定式化タイプ（例：NCWaterModel）であり、`build_method` は考慮されている問題仕様を構築するための関数（例：build_owf）です。
