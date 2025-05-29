```
@fgenerator function f(...) ... end
@fgenerator f(...) = ...
@fgenerator(generator::GeneratorType) do; ...; end
```

Define a function `f` that returns a "generator" usable with Transducers.jl-compatible APIs (akd *foldable* interface).  In `@fgenerator(generator::GeneratorType) do ... end` form, define Transducers.jl interface for `GeneratorType`.

Use [`@yield`](@ref) in the function body for producing an item.  Use `return` to finish producing items.

See also [`FGenerators`](@ref).

# Extended help

## Examples

Defining a function that returns a generator:

```jldoctest @fgenerator
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
```

Defining foldable interface for a pre-existing type:

```jldoctest @fgenerator
julia> struct Counting end;

julia> @fgenerator(itr::Counting) do
           i = 1
           while true
               @yield i
               i += 1
           end
       end;

julia> using Transducers  # for `Take`

julia> Counting() |> Take(3) |> collect
3-element Array{Int64,1}:
 1
 2
 3
```

Note that function such as `collect` and `sum` still dispatches to `iterate`-based methods (above `Counting` example worked because `Counting` was wrapped by `Take`).  To automatically dispatch to `foldl`-based methods, use `Foldable` as the supertype:

```jldoctest @fgenerator
julia> struct Count <: Foldable
           start::Int
           stop::Int
       end;

julia> @fgenerator(itr::Count) do
           i = itr.start
           i > itr.stop && return
           while true
               @yield i
               i == itr.stop && break
               i += 1
           end
       end;

julia> collect(Count(0, 2))
3-element Array{Int64,1}:
 0
 1
 2
```
