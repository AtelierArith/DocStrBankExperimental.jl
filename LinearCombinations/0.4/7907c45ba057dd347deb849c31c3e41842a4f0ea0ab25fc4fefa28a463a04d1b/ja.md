```
Linear1{T,R} <: AbstractLinear{T,R}

Linear1{T,R}(itr)
```

イテレータ `itr` によって提供された項-係数ペアから、項タイプ `T` と係数タイプ `R` の `Linear1` 型の線形結合を構築します。

このタイプの線形結合は、同時に最大で1つの非ゼロ項-係数ペアを保持できます。これが十分な場合が多く、その場合 `Linear1` は `Linear` や `DenseLinear` よりもはるかに効率的です。

このコンストラクタの他の使い方については `AbstractLinear` の下で説明されています。

関連情報としては [`AbstractLinear`](@ref), [`Linear`](@ref), [`DenseLinear`](@ref) を参照してください。

# 例

```jldoctest
julia> a = Linear1('x' => 1)
Linear1{Char, Int64} with 1 term:
'x'

julia> add!(a, 'x')
Linear1{Char, Int64} with 1 term:
2*'x'

julia> addmul!(a, 'x', -2)
Linear1{Char, Int64} with 0 terms:
0

julia> a + 'y'   # works because a is zero
Linear1{Char, Int64} with 1 term:
'y'

julia> a + 'y' + 'z'
ERROR: Linear1 cannot store linear combinations of two or more elements
[...]

julia> a = Linear1('x' => 1); b = Linear1('y' => 2); a+b
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> typeof(ans)
Linear{Char, Int64}
```
