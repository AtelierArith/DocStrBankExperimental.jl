```julia
GalleryMacroElementOperator(
    name,
    numbernodes1d,
    numberquadraturepoints1d,
    numberelements1d,
    mesh;
    mapping = nothing,
    parameters = nothing,
)
```

オプションのギャラリーからの有限要素オペレーター

# 引数:

  * `name::String`:                   オペレーターの名前を含む文字列
  * `numbernodes1d::Int`:             TensorH1LagrangeBasisの多項式次数
  * `numberquadraturepoints1d::Int`:  基底の1次元の数値積分点の数
  * `numberelements1d::Int`:          マクロ要素の要素数
  * `mesh::Mesh`:                     オペレーターのメッシュ

# キーワード引数:

  * `mapping::Union{Tuple{Function,Function},Nothing} = nothing`:  数値積分点のマッピング - ソーセージ、コスロフ-タレザー、ヘイル-トレフェセンストリップ、または変換なし
  * `parameters::Union{NamedTuple,Nothing}` = nothing:             モデルパラメータの名前付きタプル

# 戻り値:

  * 有限要素オペレーターオブジェクト

# 質量行列の例:

```jldoctest
# セットアップ
mesh = Mesh2D(1.0, 1.0);
mass = GalleryMacroElementOperator("mass", 4, 4, 2, mesh);

# 検証
println(mass)

# 出力

有限要素オペレーター:
2d メッシュ:
    dx: 1.0
    dy: 1.0

2 入力:
オペレーターフィールド:
  マクロ要素テンソル積基底:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  評価モード:
    補間
オペレーターフィールド:
  マクロ要素テンソル積基底:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  評価モード:
    数値積分重み

1 出力:
オペレーターフィールド:
  マクロ要素テンソル積基底:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  評価モード:
    補間
```

# 拡散オペレーターの例:

```jldoctest
# セットアップ
mesh = Mesh2D(1.0, 1.0);
diffusion = GalleryMacroElementOperator("diffusion", 4, 4, 2, mesh);

# 検証
println(diffusion)

# 出力

有限要素オペレーター:
2d メッシュ:
    dx: 1.0
    dy: 1.0

2 入力:
オペレーターフィールド:
  マクロ要素テンソル積基底:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  評価モード:
    勾配
オペレーターフィールド:
  マクロ要素テンソル積基底:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  評価モード:
    数値積分重み

1 出力:
オペレーターフィールド:
  マクロ要素テンソル積基底:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  評価モード:
    勾配
```

# 伝播オペレーターの例:

```jldoctest
# セットアップ
mesh = Mesh2D(1.0, 1.0);
advection = GalleryVectorOperator("advection", 4, 4, 1, mesh);

# 検証
println(advection)

# 出力

有限要素オペレーター:
2d メッシュ:
    dx: 1.0
    dy: 1.0

2 入力:
オペレーターフィールド:
  テンソル積基底:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  評価モード:
    補間
オペレーターフィールド:
  テンソル積基底:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  評価モード:
    数値積分重み

1 出力:
オペレーターフィールド:
  テンソル積基底:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  評価モード:
    勾配
```
