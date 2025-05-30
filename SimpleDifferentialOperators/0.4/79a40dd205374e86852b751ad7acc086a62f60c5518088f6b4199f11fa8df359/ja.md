```
extrapolatetoboundary(v, x̄, bc::Tuple{Reflecting, Reflecting})
```

`length(x̄)`のベクトルを返し、その`2:(length(x̄)-1)`の要素は`v`であり、最初と最後の要素は境界条件`bc`に従って`x̄`の境界で外挿された`v`です。

`bc`の最初の要素は下限に適用され、`bc`の2番目の要素は上限に適用されます。

# 例

```jldoctest; setup = :(using SimpleDifferentialOperators)
julia> x̄ = 0:5
0:5

julia> x = interiornodes(x̄)
1
2
3

julia> v = (x -> x^2).(x)
5-element Array{Int64,1}:
  1
  4
  9
 16
 25

julia> extrapolatetoboundary(v, x̄, (Reflecting(), Reflecting()))
7-element Array{Int64,1}:
  1
  1
  4
  9
 16
 25
 25
```
