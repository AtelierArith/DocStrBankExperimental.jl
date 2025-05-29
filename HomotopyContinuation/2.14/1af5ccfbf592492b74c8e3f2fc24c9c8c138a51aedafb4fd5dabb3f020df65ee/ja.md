```
rand_subspace(n::Integer; dim | codim, affine = true, real = false)
```

与えられた次元 `dim` またはコダイメンション `codim`（どちらか一方を提供する必要があります）を持つランダムな [`LinearSubspace`](@ref) を次元 `n` の周囲空間で生成します。`real` が `true` の場合、外的記述は実数になります。`affine` の場合、アフィン線形部分空間が生成されます。部分空間は、`randn` を使用して外的記述の各エントリを独立に正規分布から引くことによって生成されます。

```
rand_subspace(x::AbstractVector; dim | codim, affine = true)
```

与えられた点 `x` を通る、次元 `dim` またはコダイメンション `codim`（どちらか一方を提供する必要があります）を持つランダムな [`LinearSubspace`](@ref) を次元 `length(x)` の周囲空間で生成します。

## 例

一般的なランダム部分空間の構築:

```julia-repl
julia> rand_subspace(3; dim = 1)
1-dim. (affine) linear subspace {x|Ax=b} with eltype Complex{Float64}:
A:
2×3 Array{Complex{Float64},2}:
  -1.73825+1.27987im   -0.0871343+0.840408im  -0.551957+0.106397im
 -0.597132-0.343965im   -0.122543-0.172715im   -1.04949+0.370917im
b:
2-element Array{Complex{Float64},1}:
  0.47083334430689394 + 0.8099804422599071im
 -0.12018696822943896 + 0.11723026326952792im

julia> rand_subspace(4; codim = 1)
3-dim. (affine) linear subspace {x|Ax=b} with eltype Complex{Float64}:
A:
1×4 Array{Complex{Float64},2}:
 0.345705+0.0893881im  -0.430867-0.663249im  0.979969-0.569378im  -0.29722-0.192493im
b:
1-element Array{Complex{Float64},1}:
 0.7749708228192062 + 0.9762873764567546im
```
