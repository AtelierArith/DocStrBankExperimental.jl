```
withgradient(f, args::Union{Const,Duplicated}...)
```

This should return the same answer as `withgradient(f, model, args...)`, but it uses Enzyme.jl instead of Zygote.jl to compute the derivative.

Only available when Enzyme is loaded!

!!! warning "Experimental"
    Enzyme support like this is new and somewhat experimental. This method was added in Flux 0.15.


# Example

```julia-repl
julia> using Flux, Enzyme

julia> model = Chain(Embedding([1.1 2.2 3.3]), Dense([4.4;;]), only);

julia> model(3)
14.52

julia> Flux.withgradient(m -> m(3), model)  # this uses Zygote
(val = 14.52, grad = ((layers = ((weight = [0.0 0.0 4.4],), (weight = [3.3;;], bias = [1.0], σ = nothing), nothing),),))

julia> Flux.withgradient(m -> m(3), Duplicated(model))  # this uses Enzyme
(val = 14.52, grad = ((layers = ((weight = [0.0 0.0 4.4],), (weight = [3.3;;], bias = [1.0], σ = nothing), nothing),),))
```

The function `f` may return Tuple or NamedTuple, with the loss as the first element. The gradient is then `grad = gradient(first∘f, args...)` but the returned value is `val = f(args...)`:

```julia-repl
julia> Flux.withgradient(m -> (m(3), "aux"), Duplicated(model))
(val = (14.52, "aux"), grad = ((layers = ((weight = [0.0 0.0 4.4],), (weight = [3.3;;], bias = [1.0], σ = nothing), nothing),),))

julia> Flux.withgradient(m -> (loss=m(3), aux=round.(m.(1:3); digits=3)), Duplicated(model))
(val = (loss = 14.52, aux = [4.84, 9.68, 14.52]), grad = ((layers = ((weight = [0.0 0.0 4.4],), (weight = [3.3;;], bias = [1.0], σ = nothing), nothing),),))
```
