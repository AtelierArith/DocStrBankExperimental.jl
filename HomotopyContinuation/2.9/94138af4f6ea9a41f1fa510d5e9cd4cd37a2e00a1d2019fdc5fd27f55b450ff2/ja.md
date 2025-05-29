```
LinearSubspace(A, b)
```

$$
n
$$

次元空間における$m$次元（アフィン）線形部分空間$L$は、外的記述によって与えられます。$L = \{ x | A x = b \}$。

```julia-repl
julia> A = LinearSubspace([1 0 3; 2 1 3], [5, -2])
1次元の（アフィン）線形部分空間 {x|Ax=b} で、eltypeはFloat64です：
A:
2×3 Array{Float64,2}:
 1.0  0.0  3.0
 2.0  1.0  3.0
b:
2要素のArray{Float64,1}:
  5.0
 -2.0

julia> dim(A)
1

julia> codim(A)
2

julia> ambient_dim(A)
3
```

`LinearSubspace`は常にその[`extrinsic`](@ref)記述を保持します。[`ExtrinsicDescription`](@ref)も参照してください。また、その[`intrinsic`](@ref)記述も保持します。[`IntrinsicDescription`](@ref)を参照してください。

```julia-repl
julia> intrinsic(A)
IntrinsicDescription{Float64}:
A:
3×1 Array{Float64,2}:
 -0.6882472016116853
  0.6882472016116853
  0.22941573387056186
b₀:
3要素のArray{Float64,1}:
 -3.0526315789473677
 -3.947368421052632
  2.684210526315789
```

`LinearSubspace`は、[`Intrinsic`](@ref)または[`Extrinsic`](@ref)座標を使用して評価できます。

```julia-repl
julia> u = [0.5]
1要素のArray{Float64,1}:
 0.5

julia> x = A(u, Intrinsic)
3要素のArray{Float64,1}:
 -3.3967551797532103
 -3.6032448202467893
  2.79891839325107

julia> A(x, Extrinsic)
  2要素のArray{Float64,1}:
   0.0
   0.0
```

使用する座標を変更するには、[`coord_change`](@ref)を使用できます。

```julia-repl
julia> coord_change(A, Extrinsic, Intrinsic, x)
1要素のArray{Float64,1}:
 0.49999999999999994
```
