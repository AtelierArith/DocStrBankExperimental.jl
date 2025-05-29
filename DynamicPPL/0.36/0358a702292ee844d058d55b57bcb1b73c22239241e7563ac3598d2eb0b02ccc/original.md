```
@submodel model
@submodel ... = model
```

Run a Turing `model` nested inside of a Turing model.

!!! warning
    This is deprecated and will be removed in a future release. Use `left ~ to_submodel(model)` instead (see [`to_submodel`](@ref)).


# Examples

```jldoctest submodel; setup=:(using Distributions)
julia> @model function demo1(x)
           x ~ Normal()
           return 1 + abs(x)
       end;

julia> @model function demo2(x, y)
            @submodel a = demo1(x)
            return y ~ Uniform(0, a)
       end;
```

When we sample from the model `demo2(missing, 0.4)` random variable `x` will be sampled:

```jldoctest submodel
julia> vi = VarInfo(demo2(missing, 0.4));
┌ Warning: `@submodel model` and `@submodel prefix=... model` are deprecated; see `to_submodel` for the up-to-date syntax.
│   caller = ip:0x0
└ @ Core :-1

julia> @varname(x) in keys(vi)
true
```

Variable `a` is not tracked since it can be computed from the random variable `x` that was tracked when running `demo1`:

```jldoctest submodel
julia> @varname(a) in keys(vi)
false
```

We can check that the log joint probability of the model accumulated in `vi` is correct:

```jldoctest submodel
julia> x = vi[@varname(x)];

julia> getlogp(vi) ≈ logpdf(Normal(), x) + logpdf(Uniform(0, 1 + abs(x)), 0.4)
true
```
