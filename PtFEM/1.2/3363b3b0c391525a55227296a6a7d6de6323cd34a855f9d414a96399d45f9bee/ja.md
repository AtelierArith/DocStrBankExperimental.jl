# p44

弾性剛接合フレームの分析は、2ノードフレーム構造要素と2次元または3次元の線形有限要素を使用します。

### コンストラクタ

```julia
p44(data)
```

### 引数

```julia
* `data::Dict{Symbol, Any}` : すべての入力データを含む辞書
```

### 辞書のキー

```julia
* struc_el::StructuralElement                          : 構造有限要素のタイプ
* support::Array{Tuple{Int,Array{Int,1}},1}        : 固定変位ベクトル
* loaded_nodes::Array{Tuple{Int,Array{Float64,1}},1} : ノード荷重ベクトル
* properties::Vector{Float64}                          : 材料特性
* x_coords::FloatRange{Float64}                        : x座標ベクトル
* y_coords::FloatRange{Float64}                        : y座標ベクトル
* g_num::Array{Int,2}                                : 要素ノード接続
* fixed_freedoms::Array{Tuple{Vector{Int}}           : 固定自由度
```

### オプションの追加辞書キー

```julia
* etype::Vector{Int}                                 : 要素材料ベクトル
* penalty::Float64                                     : 固定自由度のペナルティ
* z_coords::FloatRange{Float64}                        : z座標ベクトル
* eq_nodal_forces_and_moments                          : 等価ノード荷重
```

### 戻り値

```julia
* (jfem, dis_df, fm_df)        : jfem、dis_df、およびfm_dfのタプル
                                 ここで:
                                    jfem::jFem    : 計算結果のタイプ
                                    dis_df        : 変位データテーブル
                                    fm_df         : 力とモーメントのデータテーブル
```

### 関連ヘルプ

```julia
?StructuralElement  : 構造要素に関するヘルプ
?Beam               : ビーム構造有限要素に関するヘルプ
?FiniteElement      : 有限要素タイプに関するヘルプ
```
