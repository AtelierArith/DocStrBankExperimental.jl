```
coordinates(a::DenseLinear{T,R}) -> AbstractArray{R}
```

`a`の基底に対する座標を返します。座標配列（通常はベクトル）は基底と同じ軸を持っています。この配列を変更すると、`a`も変更されます。

関連情報は[`basis`](@ref)を参照してください。

# 例

```jldoctest
julia> b = Basis('x':'z')
Basis('x':1:'z')

julia> a = DenseLinear('x' => 1, 'z' => 2; basis = b)
DenseLinear{Char, Int64} with 2 terms:
'x'+2*'z'

julia> v = coordinates(a)
3-element Vector{Int64}:
 1
 0
 2

julia> a == Linear(x => c for (x, c) in zip(basis(a), v))
true

julia> v[2] = -1; a
DenseLinear{Char, Int64} with 3 terms:
'x'-'y'+2*'z'
```
