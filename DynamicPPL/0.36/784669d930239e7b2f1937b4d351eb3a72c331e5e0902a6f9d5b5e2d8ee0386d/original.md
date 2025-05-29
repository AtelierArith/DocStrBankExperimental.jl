```
struct Model{F,argnames,defaultnames,missings,Targs,Tdefaults,Ctx<:AbstractContext}
    f::F
    args::NamedTuple{argnames,Targs}
    defaults::NamedTuple{defaultnames,Tdefaults}
    context::Ctx=DefaultContext()
end
```

A `Model` struct with model evaluation function of type `F`, arguments of names `argnames` types `Targs`, default arguments of names `defaultnames` with types `Tdefaults`, missing arguments `missings`, and evaluation context of type `Ctx`.

Here `argnames`, `defaultargnames`, and `missings` are tuples of symbols, e.g. `(:a, :b)`. `context` is by default `DefaultContext()`.

An argument with a type of `Missing` will be in `missings` by default. However, in non-traditional use-cases `missings` can be defined differently. All variables in `missings` are treated as random variables rather than observations.

The default arguments are used internally when constructing instances of the same model with different arguments.

# Examples

```julia
julia> Model(f, (x = 1.0, y = 2.0))
Model{typeof(f),(:x, :y),(),(),Tuple{Float64,Float64},Tuple{}}(f, (x = 1.0, y = 2.0), NamedTuple())

julia> Model(f, (x = 1.0, y = 2.0), (x = 42,))
Model{typeof(f),(:x, :y),(:x,),(),Tuple{Float64,Float64},Tuple{Int64}}(f, (x = 1.0, y = 2.0), (x = 42,))

julia> Model{(:y,)}(f, (x = 1.0, y = 2.0), (x = 42,)) # with special definition of missings
Model{typeof(f),(:x, :y),(:x,),(:y,),Tuple{Float64,Float64},Tuple{Int64}}(f, (x = 1.0, y = 2.0), (x = 42,))
```
