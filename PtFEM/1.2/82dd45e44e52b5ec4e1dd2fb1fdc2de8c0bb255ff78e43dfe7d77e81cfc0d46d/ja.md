# メソッド p41

軸方向に荷重がかかった弾性ロッドの一次元解析を2ノード線要素を使用して行います。

### コンストラクタ

```julia
p41(data)
```

### 引数

```julia
* `data::Dict{Symbol, Any}`  : すべての入力データを含む辞書
```

### 必要なデータ辞書キー

```julia
* struc_el::StructuralElement                          : 構造的フィン要素のタイプ
* support::Array{Tuple{Int,Array{Int,1}},1}        : 固定変位ベクトル
* loaded_nodes::Array{Tuple{Int,Array{Float64,1}},1} : ノード荷重ベクトル
* properties::Vector{Float64}                          : 材料特性
* x_coords::FloatRange{Float64}                        : x座標ベクトル
```

### オプションの追加データ辞書キー

```julia
* penalty = 1e20               : 自由度が固定された場合に使用されるペナルティ
* etype::Vector{Int}         : np_types > 1 の場合の要素材料ベクトル
* eq_nodal_forces_and_moments  : 荷重ノードへの分布荷重の寄与
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
?StructuralElement             : 利用可能な構造要素タイプのリスト
?Rod                           : ロッド構造要素に関するヘルプ
?FiniteElement                 : 有限要素タイプのリスト
?Line                          : 線有限要素に関するヘルプ
```
