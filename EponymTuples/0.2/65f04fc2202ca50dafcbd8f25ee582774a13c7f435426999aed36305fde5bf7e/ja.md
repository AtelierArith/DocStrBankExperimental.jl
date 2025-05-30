```
@eponymargs(a, b::T, ...)
```

は、`((a, b)::NamedTuple{(:a, :b), <: Tuple{Any, T}})` のような形式に展開され、変数名 *両方* を `NamedTuple` と関数引数のデコンストラクションに使用します。

有効な引数は変数名、または型指定子に続く名前です（指定がない場合は `Any` が使用されます）。

# 例

```jldoctest
julia> using EponymTuples

julia> foo(@eponymargs(a, b)) = a + b
foo (generic function with 1 method)

julia> foo((a = 1, b = 2))
3
```
