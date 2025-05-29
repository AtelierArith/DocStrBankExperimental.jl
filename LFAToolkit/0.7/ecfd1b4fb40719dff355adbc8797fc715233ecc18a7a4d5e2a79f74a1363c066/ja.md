```julia
GalleryVectorOperator(name, numbernodes1d, numberquadraturepoints1d, numberelements1d, mesh)
```

オプションのギャラリーからの有限要素オペレーター

# 引数:

  * `name::String`:                   オペレーターの名前を含む文字列
  * `numbernodes1d::Int`:             TensorH1LagrangeBasisの多項式次数
  * `numberquadraturepoints1d::Int`:  基底の1次元における数値積分点の数
  * `numbercomponents::Int`:          コンポーネントの数
  * `mesh::Mesh`:                     オペレーターのメッシュ

# 戻り値:

  * 有限要素オペレーターオブジェクト

# 質量行列の例:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
mass = GalleryVectorOperator("mass", 4, 4, 3, mesh);

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
    numbercomponents: 3
    dimension: 2
  evaluation mode:
    interpolation
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 3
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 3
    dimension: 2
  evaluation mode:
    interpolation
```

# 拡散オペレーターの例:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
diffusion = GalleryVectorOperator("diffusion", 4, 4, 3, mesh);

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
    numbercomponents: 3
    dimension: 2
  evaluation mode:
    gradient
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 3
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 3
    dimension: 2
  evaluation mode:
    gradient
```
