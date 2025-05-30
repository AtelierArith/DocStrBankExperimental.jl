```
skipnan(itr)
```

`itr`内の要素を反復処理し、NaN値をスキップするイテレータを返します。返されるオブジェクトは、`itr`がインデックス可能であれば、`itr`のインデックスを使用してインデックス付けできます。NaN値に対応するインデックスは無効です：それらは[`keys`](@ref)および[`eachindex`](@ref)によってスキップされ、使用しようとすると`ErrorException`がスローされます。`collect`を使用して、`itr`内の非NaN値を含む`Array`を取得します。`itr`が多次元配列であっても、入力の次元を保持しながらNaNを削除することは不可能なため、結果は常に`Vector`になります。

# 例

```jldoctest
julia> x = skipnan([1, NaN, 2])
skipnan([1.0, NaN, 2.0])
julia> sum(x)
3
julia> x[1]
1
julia> x[2]
ERROR: the value at index (2,) is NaN
[...]
julia> argmax(x)
3
julia> collect(keys(x))
2-element Vector{Int64}:
 1
 3
julia> collect(skipnan([1, NaN, 2]))
2-element Vector{Float64}:
 1.0
 2.0
julia> collect(skipnan([1 NaN; 2 NaN]))
2-element Vector{Float64}:
 1.0
 2.0
```
