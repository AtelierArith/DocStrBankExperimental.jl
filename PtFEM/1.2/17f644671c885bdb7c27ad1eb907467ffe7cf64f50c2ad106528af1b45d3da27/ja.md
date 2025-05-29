# メソッド p45

1、2、または3次元の2ノードフレーム構造要素を使用した弾塑性ビームまたは剛接合フレームの解析。

### コンストラクタ

```julia
p45(data)
```

### 引数

```julia
* `data::Dict{Symbol, Any}`  : すべての入力データを含む辞書
```

### 必要なデータ辞書キー

```julia
* struc_el::StructuralElement                          : 構造要素のタイプ
* support::Array{Tuple{Int,Array{Int,1}},1}        : 固定変位ベクトル
* loaded_nodes::Array{Tuple{Int,Array{Float64,1}},1} : ノード荷重ベクトル
* properties::Vector{Float64}                          : 材料特性
* x_coords::FloatRange{Float64}                        : x座標ベクトル
* dload::FloatRange{Float64}                           : 荷重ステップ
```

### オプションの追加データ辞書キー

```julia
* penalty = 1e20                 : 自由度が固定された場合に使用されるペナルティ
* etype::Vector{Int}           : np_types > 1 の場合の要素材料ベクトル
* y_coords::FloatRange{Float64}  : y座標ベクトル (2D)
* z_coords::FloatRange{Float64}  : x座標ベクトル (3D)
* limit = 250                    : 反復制限
* tol = 0.0001                   : 反復収束のための許容誤差
```

### 関連ヘルプ

```julia
?StructuralElement             : 利用可能な構造要素タイプのリスト
?Frame                         : フレーム構造要素に関するヘルプ
?FiniteElement                 : 有限要素タイプのリスト
?Line                          : 線形有限要素に関するヘルプ
```
