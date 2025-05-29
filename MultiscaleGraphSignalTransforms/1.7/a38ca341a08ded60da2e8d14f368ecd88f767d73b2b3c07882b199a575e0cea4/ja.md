```
(levlistfull, levlengthsfull, transfull) = bsfull(GP::GraphPart, BS::BasisSpec, trans::Vector{Bool})
```

BasisSpecオブジェクトを与えると、フルレングスの冗長levlist、levlengths、およびtransの説明を返します。

### 入力引数

  * `GP::GraphPart`: 入力GraphPartオブジェクト
  * `BS::BasisSpec`: 入力BasisSpecオブジェクト
  * `trans::Vector{Bool}`: HGLET-GHWTハイブリッド変換に使用される変換の仕様（デフォルト: null）
  * `levlengthsp::Bool`: levlengthsfullを返すフラグ（デフォルト: false）
  * `transp::Bool`: transfullを返すフラグ（デフォルト: false）

### 出力引数

  * `levlistfull::Vector{UInt8}`: フルレングスの冗長レベルリストの説明
  * `levlengthsfull::Vector{UInt8}`: フルレングスの冗長レベル長の説明
  * `transfull::Matrix{Bool}`: フルレングスの冗長transの説明
