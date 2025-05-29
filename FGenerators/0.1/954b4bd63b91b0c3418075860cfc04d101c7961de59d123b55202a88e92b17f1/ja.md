# FGenerators: `foldl` for humans™

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliafolds.github.io//FGenerators.jl/dev) [![GitHub Actions](https://github.com/JuliaFolds//FGenerators.jl/workflows/Run%20tests/badge.svg)](https://github.com/JuliaFolds//FGenerators.jl/actions?query=workflow%3ARun+tests)

FGenerators.jlは、シンプルな`@yield`ベースの構文を持つTransducers.jl互換の拡張`foldl`を定義するためのパッケージです。ここでは、アドホックな「ジェネレーター」を作成するためのいくつかの例を示します。

```jldoctest README
julia> using FGenerators

julia> @fgenerator function generate123()
           @yield 1
           @yield 2
           @yield 3
       end;

julia> collect(generate123())
3-element Array{Int64,1}:
 1
 2
 3

julia> sum(generate123())
6

julia> @fgenerator function organpipe(n::Integer)
           i = 0
           while i != n
               i += 1
               @yield i
           end
           while true
               i -= 1
               i == 0 && return
               @yield i
           end
       end;

julia> collect(organpipe(3))
5-element Array{Int64,1}:
 1
 2
 3
 2
 1

julia> @fgenerator function organpipe2(n)
           @yieldfrom 1:n
           @yieldfrom n-1:-1:1
       end;

julia> collect(organpipe2(2))
3-element Array{Int64,1}:
 1
 2
 1
```

FGenerators.jlは、[GeneratorsX.jl](https://github.com/JuliaFolds/GeneratorsX.jl)のスピンオフです。

[FLoops.jl](https://github.com/JuliaFolds/FLoops.jl)を使用して、ジェネレーターから生成されたアイテムを反復処理します。

```jldoctest README
julia> using FLoops

julia> @floop for x in generate123()
           @show x
       end
x = 1
x = 2
x = 3
```

## 既存の型にfoldプロトコルを追加する

`foldl`プロトコルは、`@fgenerator(foldable::T) do .. end`という構文を使用して、既存の型`T`に対して実装できます。

```jldoctest README
julia> struct OrganPipe <: Foldable
           n::Int
       end

julia> @fgenerator(foldable::OrganPipe) do
           n = foldable.n
           @yieldfrom 1:n
           @yieldfrom n-1:-1:1
       end;

julia> collect(OrganPipe(2))
3-element Array{Int64,1}:
 1
 2
 1
```

`Base` API（`collect`など）を使用する場合にのみ、`Foldable`を継承する必要があります。`FLoops.@floop`を含むTransducers.jl APIを使用する場合は必要ありません。

## 並列化可能なコレクションの定義

`@fgenerator`だけでは、コレクションに対して並列ループを使用するには不十分です。しかし、[`SplittablesBase.halve`](https://github.com/JuliaFolds/SplittablesBase.jl)と`length`（または`length`の定義が難しい場合は`SplittablesBase.amount`）を定義することで簡単にサポートできます。`halve`と`length`は同じ既存の型に対して実装する必要があるため、上記のように`@fgenerator(...) do`構文を使用する必要があります。上記の`OrganPipe`の例を拡張します。

```jldoctest README
julia> using SplittablesBase

julia> function SplittablesBase.halve(foldable::OrganPipe)
           n = foldable.n
           return (1:n, n-1:-1:1)
       end;

julia> Base.length(foldable::OrganPipe) = 2 * foldable.n - 1;

julia> @floop for x in OrganPipe(2)
           @reduce(s += x)
       end
       s
4
```

## `@fgenerator`内での`@floop`の使用

`@floop`は`@fgenerator`内で使用できます。

```jldoctest README
julia> @fgenerator function ffilter(f, xs)
           @floop for x in xs
               if f(x)
                   @yield x
               end
           end
       end;

julia> collect(ffilter(isodd, generate123()))
2-element Array{Int64,1}:
 1
 3

julia> collect(ffilter(isodd, organpipe(3)))
3-element Array{Int64,1}:
 1
 3
 1

julia> collect(ffilter(isodd, 1:5))  # fallback to `Base.iterate`
3-element Array{Int64,1}:
 1
 3
 5
```
