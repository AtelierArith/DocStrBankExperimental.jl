```
jmat(j::Real, which::Union{Symbol,Val})
```

高次スピン-`j` 演算子を生成します。ここで `j` はスピン量子数で、非負の整数または半整数であることができます。

パラメータ `which` は、返す演算子の種類を指定します。

  * `:x`: $\hat{S}_x$
  * `:y`: $\hat{S}_y$
  * `:z`: $\hat{S}_z$
  * `:+`: $\hat{S}_+$
  * `:-`: $\hat{S}_-$

パラメータ `which` が指定されていない場合は、スピン-`j` 演算子のセット $(\hat{S}_x, \hat{S}_y, \hat{S}_z)$ を返します。

# 例

```jldoctest
julia> jmat(0.5, :x)

Quantum Object:   type=Operator()   dims=[2]   size=(2, 2)   ishermitian=true
2×2 SparseMatrixCSC{ComplexF64, Int64} with 2 stored entries:
     ⋅      0.5+0.0im
 0.5+0.0im      ⋅

julia> jmat(0.5, Val(:-))

Quantum Object:   type=Operator()   dims=[2]   size=(2, 2)   ishermitian=false
2×2 SparseMatrixCSC{ComplexF64, Int64} with 1 stored entry:
     ⋅          ⋅    
 1.0+0.0im      ⋅

julia> jmat(1.5, Val(:z))

Quantum Object:   type=Operator()   dims=[4]   size=(4, 4)   ishermitian=true
4×4 SparseMatrixCSC{ComplexF64, Int64} with 4 stored entries:
 1.5+0.0im      ⋅           ⋅           ⋅    
     ⋅      0.5+0.0im       ⋅           ⋅    
     ⋅          ⋅      -0.5+0.0im       ⋅    
     ⋅          ⋅           ⋅      -1.5+0.0im
```

!!! warning "型の安定性に注意!"
    型の安定性を保ちたい場合は、`jmat(j, Val(which))` を使用することをお勧めします。`jmat(j, which)` の代わりに使用してください。型の安定性に関する詳細は、[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type)および[関連セクション](@ref doc:Type-Stability)を参照してください。

