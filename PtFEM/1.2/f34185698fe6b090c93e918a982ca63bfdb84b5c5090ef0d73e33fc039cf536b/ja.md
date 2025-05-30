# メソッド p63

弾塑性（モール・クーロン）材料の平面ひずみ支持力解析を8ノードの長方形四辺形を使用して行います。剛体滑らかな基礎。変位制御。粘塑性ひずみ法。

### コンストラクタ

```julia
p63(data)
```

### 引数

```julia
* `data::Dict{Symbol, Any}` : すべての入力データを含む辞書
```

### 必要なデータ辞書キー

```julia
* struc_el::StructuralElement                          : 構造要素
* properties::Vector{Float64}                          : 材料特性
* x_coords::FloatRange{Floalt64}                       : x座標ベクトル
* y_coords::FloatRange{Floalt64}                       : y座標ベクトル
```

### オプションの追加データ辞書キー

```julia
* tol::Float64                 : 収束許容値
* limit = 250                  : 繰り返し制限
* incs::Int                    : 増分荷重ステップ
* presc::Float64               : 壁の変位増分
* penalty = 1e20               : 自由度固定のために使用されるペナルティ
* etype::Vector{Int}           : np_types > 1 の場合の要素材料ベクトル
```

### 戻り値

```julia
* (g_coord, g_num, disp)        : ここで：
                                    g_coord  : 座標
                                    g_num    : ノード番号
                                    disp     : 変位の行列
```

### 関連ヘルプ

```julia
?StructuralElement             : 利用可能な構造要素タイプのリスト
?Plane                         : 平面構造要素に関するヘルプ
?FiniteElement                 : 有限要素タイプのリスト
?Quadrilateral                 : 四辺形有限要素に関するヘルプ
```
