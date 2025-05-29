# MicroCollections

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliafolds2.github.io/MicroCollections.jl/dev) [![GitHub Actions](https://github.com/JuliaFolds2/MicroCollections.jl/workflows/Run%20tests/badge.svg)](https://github.com/JuliaFolds2/MicroCollections.jl/actions?query=workflow%3A%22Run+tests%22)

MicroCollections.jlは、不変の空およびシングルトンコレクションを提供します。

```jldoctest README
julia> using MicroCollections

julia> vec0()  # または EmptyVector()
0-element EmptyVector{Union{}}

julia> vec0(Int)  # または EmptyVector{Int}()
0-element EmptyVector{Int64}

julia> vec1(1)  # または SingletonVector((1,))
1-element SingletonVector{Int64}:
 1

julia> EmptyDict()
EmptyDict{Union{},Union{}}()

julia> EmptyDict{Symbol,Char}()
EmptyDict{Symbol,Char}()

julia> SingletonDict(:a => 0)
SingletonDict{Symbol,Int64} with 1 entry:
  :a => 0

julia> EmptySet()
EmptySet{Union{}}()

julia> EmptySet{Int64}()
EmptySet{Int64}()

julia> SingletonSet((1,))
SingletonSet{Int64} with 1 element:
  1
```

BangBang.jlを使用すると、MicroCollections.jlは、reduceと組み合わせることができるシングルトンソリューションを構築するのに役立ちます。

```jldoctest README
julia> using BangBang.Experimental: mergewith!!

julia> @assert mapreduce(
           x -> SingletonDict(abs(x) % 10 => 1), mergewith!!(+), 1:1000,
       ) == Dict(
           0 => 100,
           1 => 100,
           2 => 100,
           3 => 100,
           4 => 100,
           5 => 100,
           6 => 100,
           7 => 100,
           8 => 100,
           9 => 100,
       )
```
