```julia
struct CustomAlgorithmDefault{I<:ModelWrappers.AbstractInitialization, U<:BaytesCore.UpdateBool}
```

Customコンストラクタのデフォルト引数。

# フィールド

  * `init::ModelWrappers.AbstractInitialization`: 初期モデルパラメータを取得するためのメソッド、'AbstractInitialization'を参照してください。
  * `generated::BaytesCore.UpdateBool`: 対応するモデルのためにgenerate(_rng, objective)がアルゴリズム診断に保存されているかどうかのブール値。
