# DataTools: フラットテーブルとネストされたデータ構造をTransducers.jlを使用して操作する

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliafolds.github.io/DataTools.jl/dev) [![GitHub Actions](https://github.com/JuliaFolds/DataTools.jl/workflows/Run%20tests/badge.svg)](https://github.com/JuliaFolds/DataTools.jl/actions?query=workflow%3A%22Run+tests%22)

```jldoctest README
julia> using DataTools: oncol, modifying, averaging

julia> using Transducers: Filter

julia> data = [(a = 1, b = 7), (a = 2, b = 3), (a = 3, b = 4)];

julia> rf = oncol(a = +, b = averaging);

julia> foldl(rf, Filter(x -> isodd(x.a)), data)
(a = 4, b = 5.5)

julia> map(modifying(a = string), data)
3-element Array{NamedTuple{(:a, :b),Tuple{String,Int64}},1}:
 (a = "1", b = 7)
 (a = "2", b = 3)
 (a = "3", b = 4)

julia> reduce(modifying(a = +), data)
(a = 6, b = 7)

julia> using Accessors: @optic

julia> data = [(a = ((b = 1,), 2),), (a = ((b = 3,), 4),)];

julia> map(modifying(@optic(_.a[1].b) => x -> 10x), data)
2-element Array{NamedTuple{(:a,),Tuple{Tuple{NamedTuple{(:b,),Tuple{Int64}},Int64}}},1}:
 (a = ((b = 10,), 2),)
 (a = ((b = 30,), 4),)
```
