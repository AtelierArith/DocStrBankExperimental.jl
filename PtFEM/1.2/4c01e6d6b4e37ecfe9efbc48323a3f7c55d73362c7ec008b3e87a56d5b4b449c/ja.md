# メソッド p47

4ノード四角形有限要素を使用したプレート（平面構造要素）の解析。均質材料で同一の要素。メッシュはxまたはy方向に番号付けされています。

### コンストラクタ

```julia
p47(data)
```

### 引数

```julia
* `data::Dict{Symbol, Any}` : すべての入力データを含む辞書
```

### 必要なデータ辞書キー

```julia
* struc_el::StructuralElement                          : 構造要素
* support::Array{Tuple{Int,Array{Int,1}},1}        : 固定変位ベクトル
* loaded_nodes::Array{Tuple{Int,Array{Float64,1}},1} : ノード荷重ベクトル
* properties::Vector{Float64}                          : 材料特性
* x_coords::FloatRange{Floalt64}                       : x座標ベクトル
* y_coords::FloatRange{Floalt64}                       : y座標ベクトル
* thickness:: Float64                                  : プレートの厚さ
```

### オプションの追加データ辞書キー

```julia
* penalty = 1e20               : 自由度が固定された場合に使用されるペナルティ
* etype::Vector{Int}         : np_types > 1 の場合の要素材料ベクトル
```

### 戻り値

```julia
* (fm_df, sigma_df)            : jFem、dis_df、および fm_df のタプル
                                  ここで:
                                    fm_df         : 力とモーメントのデータテーブル
                                    sigma_df      : 応力のデータテーブル
```

### 関連ヘルプ

```julia
?StructuralElement             : 利用可能な構造要素タイプのリスト
?Plane                         : 平面構造要素に関するヘルプ
?FiniteElement                 : 有限要素タイプのリスト
?Quadrilateral                 : 四角形有限要素に関するヘルプ
```
