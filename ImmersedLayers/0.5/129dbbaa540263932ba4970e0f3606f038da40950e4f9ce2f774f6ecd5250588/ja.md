```
ForcingModelAndRegion
```

強制モデル関数、領域、およびキャッシュを保持する型

# コンストラクタ

`ForcingModelAndRegion(model::AbstractForcingModel,cache::BasicILMCache)`

`ForcingModelAndRegion(modellist::Vector{AbstractForcingModel},cache::BasicILMCache)`

これらの形式は、一般的に追加キャッシュを構築する際に呼び出されます。また、最初の引数に `nothing` を渡すと、モデルの空のリストを優雅に生成します。
