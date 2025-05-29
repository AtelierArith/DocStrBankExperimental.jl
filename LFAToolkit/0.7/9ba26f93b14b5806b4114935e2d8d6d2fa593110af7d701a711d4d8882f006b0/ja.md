```julia
GalleryOperator(
    name,
    numbernodes1d,
    numberquadraturepoints1d,
    mesh;
    collocatedquadrature = false,
    mapping = nothing,
    parameters = nothing,
)
```

ギャラリーのオプションからの有限要素オペレーター

# 引数:

  * `name::String`:                   オペレーターの名前を含む文字列
  * `numbernodes1d::Int`:             TensorH1LagrangeBasisの多項式次数
  * `numberquadraturepoints1d::Int`:  基底の1次元における数値積分点の数
  * `mesh::Mesh`:                     オペレーターのメッシュ

# キーワード引数:

  * `collocatedquadrature::Bool = false`:                        ガウス・レジェンドルまたはガウス・レジェンドル・ロバットの数値積分点
  * `mappingUnion{Tuple{Function,Function},Nothing} = nothing`:  数値積分点のマッピング - ソーセージ、コスロフ・タレザー、ヘイル・トレフェセンストリップ、または変換なし
  * `parametersUnion{NamedTuple,Nothing} = nothing`:             モデルパラメータの名前付きタプル

# 戻り値:

  * 有限要素オペレーターオブジェクト

# 質量行列の例:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
mass = GalleryOperator("mass", 4, 4, mesh);

# verify
println(mass)

# output

finite element operator:
2d mesh:
    dx: 1.0
    dy: 1.0

2 inputs:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    interpolation
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    interpolation
```

# 拡散オペレーターの例:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
diffusion = GalleryOperator("diffusion", 4, 4, mesh);

# verify
println(diffusion)

# output

finite element operator:
2d mesh:
    dx: 1.0
    dy: 1.0

2 inputs:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    gradient
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    gradient
```

# 伝播オペレーターの例:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
advection = GalleryOperator("advection", 4, 4, mesh);

# verify
println(advection)

# output

finite element operator:
2d mesh:
    dx: 1.0
    dy: 1.0

2 inputs:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    interpolation
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    gradient
```

# SUPG質量行列の例:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
parameters = (wind = [1.0, 1.0], τ = 1.0);
supgmass = GalleryOperator("supg mass", 4, 4, mesh, parameters = parameters);

# verify
println(supgmass)

# output

finite element operator:
2d mesh:
    dx: 1.0
    dy: 1.0

2 inputs:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    interpolation
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation modes:
    interpolation
    gradient
```

# SUPG伝播オペレーターの例:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
parameters = nothing;
supgadvection = GalleryOperator("supg advection", 4, 4, mesh, parameters = parameters);

# verify
println(supgadvection)

# output

finite element operator:
2d mesh:
    dx: 1.0
    dy: 1.0

2 inputs:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation modes:
    interpolation
    gradient
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    gradient
```
