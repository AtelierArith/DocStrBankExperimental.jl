```
列を作成する
```

列に集める。

```jldoctest make_columns
julia> using LightQuery

julia> import Compat: Iterators

julia> using Test: @inferred


julia> stable(x) = (a = x, b = x + 0.0, c = x, d = x + 0.0, e = x, f = x + 0.0);


julia> @inferred make_columns(Iterators.map(stable, 1:4))
(a = [1, 2, 3, 4], b = [1.0, 2.0, 3.0, 4.0], c = [1, 2, 3, 4], d = [1.0, 2.0, 3.0, 4.0], e = [1, 2, 3, 4], f = [1.0, 2.0, 3.0, 4.0])

julia> unstable(x) =
           if x <= 2
               (a = missing, b = string(x), d = string(x))
           else
               (a = x, b = missing, c = x)
           end;


julia> make_columns(Iterators.map(unstable, 1:4))
(d = Union{Missing, String}["1", "2", missing, missing], a = Union{Missing, Int64}[missing, missing, 3, 4], b = Union{Missing, String}["1", "2", missing, missing], c = Union{Missing, Int64}[missing, missing, 3, 4])

julia> make_columns(Iterators.filter(row -> true, Iterators.map(unstable, 1:4)))
(d = Union{Missing, String}["1", "2", missing, missing], a = Union{Missing, Int64}[missing, missing, 3, 4], b = Union{Missing, String}["1", "2", missing, missing], c = Union{Missing, Int64}[missing, missing, 3, 4])
```
