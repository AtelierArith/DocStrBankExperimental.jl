# p43

2ノードビーム構造要素と線形有限要素を使用した弾性ビームの解析。弾性基盤はオプションです。

### コンストラクタ

```julia
p43(data)
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
* x_coords::LinSpace{Float64}                          : x座標ベクトル
* g_num::Array{Int,2}                                : 要素ノード接続
* fixed_freedoms::Array{Tuple{Vector{Int}}           : 固定自由度
```

### オプションの追加辞書キー

```julia
* etype::Vector{Int}                                 : 要素材料ベクトル
* penalty::Float64                                     : 固定自由度のペナルティ
* eq_nodal_forces_and_moments                          : 等価ノード荷重
```

### 戻り値

```julia
* (jfem, dis_df, fm_df)        : jfem、dis_df、および fm_df のタプル
                                 ここで:
                                    jfem::jFem    : 計算結果のタイプ
                                    dis_df        : 変位データテーブル
                                    fm_df         : 力とモーメントのデータテーブル
```

### 関連ヘルプ

```julia
?StructuralElement  : 構造要素に関するヘルプ
?Rod                : ロッド構造有限要素に関するヘルプ
?FiniteElement      : 有限要素タイプに関するヘルプ
```
