```
macro _(body)
```

短い関数構文。引数は `body` の中にあり、最初の引数は `_`、2 番目の引数は `__` などです。`@inline` になります。

```jldoctest anonymous
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred (@_ _ + 1)(1)
2

julia> @inferred map((@_ __ - _), (1, 2), (2, 1))
(1, -1)
```

`_` 引数がない場合は、そのまま読み取ります。

```jldoctest anonymous
julia> (@_ x -> x + 1)(1)
2
```
