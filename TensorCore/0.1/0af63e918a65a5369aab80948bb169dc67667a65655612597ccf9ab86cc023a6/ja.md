```
boxdot(A,B) = A ⊡ B    # \boxdot
```

一般化された行列の乗算：`A`の最後の次元を`B`の最初の次元と契約します。`ndims(A)`および`ndims(B)`に対して任意です。両方がベクトルである場合、スカラー`== sum(A .* B)`を返します。

# 例

```jldoctest; setup=:(using TensorCore)
julia> A = rand(3,4,5); B = rand(5,6,7);

julia> size(A ⊡ B)
(3, 4, 6, 7)

julia> typeof(rand(5) ⊡ rand(5))
Float64

julia> try B ⊡ A catch err println(err) end
DimensionMismatch("neighbouring axes of `A` and `B` must match, got Base.OneTo(7) and Base.OneTo(3)")
```

これはMathematicaの関数`Dot[A, B]`と同じ動作です。Pythonの`numpy.dot(A, B)`とは異なり、`B`の最後から2番目の次元で契約しますが、他のすべての次元は保持されます。Juliaの`LinearAlgebra.dot`とは異なり、`A`を共役化しないため、これらは実数値ベクトルに対してのみ一致します。

`Adjoint`ベクトルと相互作用する際、これは常に`(x ⊡ y)' == y' ⊡ x'`を遵守し、したがって時には別の`Adjoint`ベクトルを返すことがあります。（`Transpose`についても同様です。）

```jldoctest; setup=:(using TensorCore)
julia> M = rand(5,5); v = rand(5);

julia> typeof(v ⊡ M')
Array{Float64,1}

julia> typeof(M ⊡ v')  # 前の行の随伴
Adjoint{Float64,Array{Float64,1}}

julia> typeof(v' ⊡ M')  # *と同じで、adjoint(M ⊡ v)に等しい
Adjoint{Float64,Array{Float64,1}}

julia> typeof(v' ⊡ v)
Float64
```

`boxdot!(Y,A,B)`も参照してください。これは`⊡`に対して`mul!`が`*`であるのと同じです。
