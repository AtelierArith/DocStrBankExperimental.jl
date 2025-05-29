```
gradient(f, args::Union{Const,Duplicated}...)
```

This should return the same answer as `gradient(f, args...)`, but it uses Enzyme.jl instead of Zygote.jl to compute the derivative.

Only available when Enzyme is loaded!

This method is used when at least one argument is of type `Duplicated`, and all unspecified aguments are wrapped in `Const`. Note that Enzyme's `Active` is not supported.

Besides returning the gradient, this is also stored within the `Duplicated` object. Calling `Enzyme.Duplicated(model)` allocates space for the gradient, which is zero'd befor use when calling `gradient`. With the keyword `zero=false`, the new gradient will instead be added to what is already stored.

!!! warning "Experimental"
    Enzyme support like this is new and somewhat experimental. This method was added in Flux 0.15.


# Example

```
julia> using Flux

julia> model = Chain(Dense([3.0;;]));

julia> Flux.gradient(model, [1]) do m, x  # computed using Zygote
         sum(abs2, m(x))
       end
((layers = ((weight = [6.0;;], bias = [6.0], σ = nothing),),), [18.0])

julia> using Enzyme

julia> dup_model = Duplicated(model);  # allocates space for gradient

julia> Flux.gradient(dup_model, Const([1])) do m, x  # Enzyme, returns the same
         sum(abs2, m(x))
       end
((layers = ((weight = [6.0;;], bias = [6.0], σ = nothing),),), nothing)

julia> dup_model  # same gradient is also stored within Duplicated
Duplicated(
  Chain(
    Dense(1 => 1),                      # 2 parameters
  ),
  # norm(∇) ≈ 8.49
)

julia> Flux.destructure((weight = [6.0;;], bias = [6.0]))[1] |> norm
8.48528137423857

julia> Flux.gradient(dup_model, [1]; zero=false) do m, x  # implict Const([1]), and grad accumulation
         sum(abs2, m(x))
       end
((layers = ((weight = [12.0;;], bias = [12.0], σ = nothing),),), nothing)
```
