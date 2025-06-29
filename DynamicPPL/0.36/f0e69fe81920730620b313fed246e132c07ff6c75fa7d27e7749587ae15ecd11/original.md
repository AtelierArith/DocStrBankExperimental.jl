```
to_submodel(model::Model[, auto_prefix::Bool])
```

Return a model wrapper indicating that it is a sampleable model over the return-values.

This is mainly meant to be used on the right-hand side of a `~` operator to indicate that the model can be sampled from but not necessarily evaluated for its log density.

!!! warning
    Note that some other operations that one typically associate with expressions of the form `left ~ right` such as [`condition`](@ref), will also not work with `to_submodel`.


!!! warning
    To avoid variable names clashing between models, it is recommend leave argument `auto_prefix` equal to `true`. If one does not use automatic prefixing, then it's recommended to use [`prefix(::Model, input)`](@ref) explicitly.


# Arguments

  * `model::Model`: the model to wrap.
  * `auto_prefix::Bool`: whether to automatically prefix the variables in the model using the left-hand   side of the `~` statement. Default: `true`.

# Examples

## Simple example

```jldoctest submodel-to_submodel; setup=:(using Distributions)
julia> @model function demo1(x)
           x ~ Normal()
           return 1 + abs(x)
       end;

julia> @model function demo2(x, y)
            a ~ to_submodel(demo1(x))
            return y ~ Uniform(0, a)
       end;
```

When we sample from the model `demo2(missing, 0.4)` random variable `x` will be sampled:

```jldoctest submodel-to_submodel
julia> vi = VarInfo(demo2(missing, 0.4));

julia> @varname(a.x) in keys(vi)
true
```

The variable `a` is not tracked. However, it will be assigned the return value of `demo1`, and can be used in subsequent lines of the model, as shown above.

```jldoctest submodel-to_submodel
julia> @varname(a) in keys(vi)
false
```

We can check that the log joint probability of the model accumulated in `vi` is correct:

```jldoctest submodel-to_submodel
julia> x = vi[@varname(a.x)];

julia> getlogp(vi) ≈ logpdf(Normal(), x) + logpdf(Uniform(0, 1 + abs(x)), 0.4)
true
```

## Without automatic prefixing

As mentioned earlier, by default, the `auto_prefix` argument specifies whether to automatically prefix the variables in the submodel. If `auto_prefix=false`, then the variables in the submodel will not be prefixed.

```jldoctest submodel-to_submodel-prefix; setup=:(using Distributions)
julia> @model function demo1(x)
           x ~ Normal()
           return 1 + abs(x)
       end;

julia> @model function demo2_no_prefix(x, z)
            a ~ to_submodel(demo1(x), false)
            return z ~ Uniform(-a, 1)
       end;

julia> vi = VarInfo(demo2_no_prefix(missing, 0.4));

julia> @varname(x) in keys(vi)  # here we just use `x` instead of `a.x`
true
```

However, not using prefixing is generally not recommended as it can lead to variable name clashes unless one is careful. For example, if we're re-using the same model twice in a model, not using prefixing will lead to variable name clashes: However, one can manually prefix using the [`prefix(::Model, input)`](@ref):

```jldoctest submodel-to_submodel-prefix
julia> @model function demo2(x, y, z)
            a ~ to_submodel(prefix(demo1(x), :sub1), false)
            b ~ to_submodel(prefix(demo1(y), :sub2), false)
            return z ~ Uniform(-a, b)
       end;

julia> vi = VarInfo(demo2(missing, missing, 0.4));

julia> @varname(sub1.x) in keys(vi)
true

julia> @varname(sub2.x) in keys(vi)
true
```

Variables `a` and `b` are not tracked, but are assigned the return values of the respective calls to `demo1`:

```jldoctest submodel-to_submodel-prefix
julia> @varname(a) in keys(vi)
false

julia> @varname(b) in keys(vi)
false
```

We can check that the log joint probability of the model accumulated in `vi` is correct:

```jldoctest submodel-to_submodel-prefix
julia> sub1_x = vi[@varname(sub1.x)];

julia> sub2_x = vi[@varname(sub2.x)];

julia> logprior = logpdf(Normal(), sub1_x) + logpdf(Normal(), sub2_x);

julia> loglikelihood = logpdf(Uniform(-1 - abs(sub1_x), 1 + abs(sub2_x)), 0.4);

julia> getlogp(vi) ≈ logprior + loglikelihood
true
```

## Usage as likelihood is illegal

Note that it is illegal to use a `to_submodel` model as a likelihood in another model:

```jldoctest submodel-to_submodel-illegal; setup=:(using Distributions)
julia> @model inner() = x ~ Normal()
inner (generic function with 2 methods)

julia> @model illegal_likelihood() = a ~ to_submodel(inner())
illegal_likelihood (generic function with 2 methods)

julia> model = illegal_likelihood() | (a = 1.0,);

julia> model()
ERROR: ArgumentError: `~` with a model on the right-hand side of an observe statement is not supported
[...]
```
