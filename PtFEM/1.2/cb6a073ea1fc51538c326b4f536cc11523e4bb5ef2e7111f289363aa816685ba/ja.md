# メソッド p46

弾性ビームの安定性（座屈）解析を2ノードビーム構造要素と線形有限要素を使用して行います。弾性基礎はオプションです。

### コンストラクタ

```julia
p46(data)
```

### 引数

```julia
* `data::Dict{Symbol, Any}` : すべての入力データを含む辞書
```

### 必要なデータ辞書キー

```julia
* struc_el::StructuralElement                          : 構造的 fin_el のタイプ
* support::Array{Tuple{Int,Array{Int,1}},1}        : 固定変位ベクトル
* properties::Vector{Float64}                          : 材料特性
* x_coords::FloatRange{Float64}                        : x座標ベクトル
```

### オプションの追加データ辞書キー

```julia
* etype::Vector{Int}         : np_types > 1 の場合の要素材料ベクトル
* limit = 250                  : 繰り返し制限
* tol = 0.0001                 : 繰り返し収束のための許容誤差
```

### 関連ヘルプ

```julia
?StructuralElement             : 利用可能な構造要素タイプのリスト
?Beam                          : ビーム構造要素に関するヘルプ
?FiniteElement                 : 有限要素タイプのリスト
?Line                          : 線形有限要素に関するヘルプ
```
