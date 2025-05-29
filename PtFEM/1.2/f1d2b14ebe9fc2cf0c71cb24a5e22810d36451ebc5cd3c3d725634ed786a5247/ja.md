# メソッド p42

2次元または3次元の2ノードロッド要素を使用した弾性ピン接合フレームの解析。

### コンストラクタ

```julia
p42(data)
```

### 引数

```julia
* `data::Dict{Symbol, Any}`  : すべての入力データを含む辞書
```

### 辞書のキー

```julia
* struc_el::StructuralElement                          : 構造要素のタイプ
* support::Array{Tuple{Int,Array{Int,1}},1}        : 固定変位ベクトル
* loaded_nodes::Array{Tuple{Int,Array{Float64,1}},1} : ノード荷重ベクトル
* properties::Vector{Float64}                          : 材料特性
* x_coords::Vector{Float64}                            : x座標ベクトル
* y_coords::Vector{Float64}                            : y座標ベクトル
* g_num::Array{Int,2}                                : 要素ノード接続
```

### オプションの追加辞書キー

```julia
* penalty::Float64             : 固定自由度のペナルティ
* etype::Vector{Int}         : 要素材料ベクトル
* z_coords::Vector{Float64}    : z座標ベクトル (3D)
* eq_nodal_forces_and_moments  : 荷重ノードへの分布荷重の寄与
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
?StructuralElement  : 構造要素タイプのリスト
?Frame              : ロッド構造フィン要素に関するヘルプ
?FiniteElement      : 有限要素タイプのリスト
?Line               : 線形有限要素に関するヘルプ
```
