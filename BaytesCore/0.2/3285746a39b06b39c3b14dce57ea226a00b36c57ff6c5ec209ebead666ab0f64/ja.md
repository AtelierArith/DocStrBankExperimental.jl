```julia
struct DataTune{D<:BaytesCore.DataStructure, C<:Union{Nothing, BaytesCore.ArrayConfig}, M}
```

データ調整構造体。

データ構造に関する情報を含みます。

# フィールド

  * `structure::BaytesCore.DataStructure`: DataStructureのサブタイプ
  * `config::Union{Nothing, BaytesCore.ArrayConfig}`: データ次元の設定。
  * `miss::Any`: 欠損データの処理。
