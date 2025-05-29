```
condition(model::Model; values...)
condition(model::Model, values::NamedTuple)
```

Return a `Model` which now treats the variables in `values` as observations.

See also: [`decondition`](@ref), [`conditioned`](@ref)

# Limitations

This does currently *not* work with variables that are provided to the model as arguments, e.g. `@model function demo(x) ... end` means that `condition` will not affect the variable `x`.

Therefore if one wants to make use of `condition` and [`decondition`](@ref) one should not be specifying any random variables as arguments.

This is done for the sake of backwards compatibility.

# Examples

## Simple univariate model

```jldoctest condition
julia> using Distributions

julia> @model function demo()
           m ~ Normal()
           x ~ Normal(m, 1)
           return (; m=m, x=x)
       end
demo (generic function with 2 methods)

julia> model = demo();

julia> m, x = model(); (m ≠ 1.0 && x ≠ 100.0)
true

julia> # Create a new instance which treats `x` as observed
       # with value `100.0`, and similarly for `m=1.0`.
       conditioned_model = condition(model, x=100.0, m=1.0);

julia> m, x = conditioned_model(); (m == 1.0 && x == 100.0)
true

julia> # Let's only condition on `x = 100.0`.
       conditioned_model = condition(model, x = 100.0);

julia> m, x =conditioned_model(); (m ≠ 1.0 && x == 100.0)
true

julia> # We can also use the nicer `|` syntax.
       conditioned_model = model | (x = 100.0, );

julia> m, x = conditioned_model(); (m ≠ 1.0 && x == 100.0)
true
```

The above uses a `NamedTuple` to hold the conditioning variables, which allows us to perform some additional optimizations; in many cases, the above has zero runtime-overhead.

But we can also use a `Dict`, which offers more flexibility in the conditioning (see examples further below) but generally has worse performance than the `NamedTuple` approach:

```jldoctest condition
julia> conditioned_model_dict = condition(model, Dict(@varname(x) => 100.0));

julia> m, x = conditioned_model_dict(); (m ≠ 1.0 && x == 100.0)
true

julia> # There's also an option using `|` by letting the right-hand side be a tuple
       # with elements of type `Pair{<:VarName}`, i.e. `vn => value` with `vn isa VarName`.
       conditioned_model_dict = model | (@varname(x) => 100.0, );

julia> m, x = conditioned_model_dict(); (m ≠ 1.0 && x == 100.0)
true
```

## Condition only a part of a multivariate variable

Not only can be condition on multivariate random variables, but we can also use the standard mechanism of setting something to `missing` in the call to `condition` to only condition on a part of the variable.

```jldoctest condition
julia> @model function demo_mv(::Type{TV}=Float64) where {TV}
           m = Vector{TV}(undef, 2)
           m[1] ~ Normal()
           m[2] ~ Normal()
           return m
       end
demo_mv (generic function with 4 methods)

julia> model = demo_mv();

julia> conditioned_model = condition(model, m = [missing, 1.0]);

julia> # (✓) `m[1]` sampled while `m[2]` is fixed
       m = conditioned_model(); (m[1] ≠ 1.0 && m[2] == 1.0)
true
```

Intuitively one might also expect to be able to write `model | (m[1] = 1.0, )`. Unfortunately this is not supported as it has the potential of increasing compilation times but without offering any benefit with respect to runtime:

```jldoctest condition
julia> # (×) `m[2]` is not set to 1.0.
       m = condition(model, var"m[2]" = 1.0)(); m[2] == 1.0
false
```

But you *can* do this if you use a `Dict` as the underlying storage instead:

```jldoctest condition
julia> # Alternatives:
       # - `model | (@varname(m[2]) => 1.0,)`
       # - `condition(model, Dict(@varname(m[2] => 1.0)))`
       # (✓) `m[2]` is set to 1.0.
       m = condition(model, @varname(m[2]) => 1.0)(); (m[1] ≠ 1.0 && m[2] == 1.0)
true
```

## Nested models

`condition` of course also supports the use of nested models through the use of [`@submodel`](@ref).

```jldoctest condition
julia> @model demo_inner() = m ~ Normal()
demo_inner (generic function with 2 methods)

julia> @model function demo_outer()
           @submodel m = demo_inner()
           return m
       end
demo_outer (generic function with 2 methods)

julia> model = demo_outer();

julia> model() ≠ 1.0
true

julia> conditioned_model = model | (m = 1.0, );

julia> conditioned_model()
1.0
```

But one needs to be careful when prefixing variables in the nested models:

```jldoctest condition
julia> @model function demo_outer_prefix()
           @submodel prefix="inner" m = demo_inner()
           return m
       end
demo_outer_prefix (generic function with 2 methods)

julia> # (×) This doesn't work now!
       conditioned_model = demo_outer_prefix() | (m = 1.0, );

julia> conditioned_model() == 1.0
false

julia> # (✓) `m` in `demo_inner` is referred to as `inner.m` internally, so we do:
       conditioned_model = demo_outer_prefix() | (var"inner.m" = 1.0, );

julia> conditioned_model()
1.0

julia> # Note that the above `var"..."` is just standard Julia syntax:
       keys((var"inner.m" = 1.0, ))
(Symbol("inner.m"),)
```

And similarly when using `Dict`:

```jldoctest condition
julia> conditioned_model_dict = demo_outer_prefix() | (@varname(var"inner.m") => 1.0);

julia> conditioned_model_dict()
1.0
```

The difference is maybe more obvious once we look at how these different in their trace/`VarInfo`:

```jldoctest condition
julia> keys(VarInfo(demo_outer()))
1-element Vector{VarName{:m, typeof(identity)}}:
 m

julia> keys(VarInfo(demo_outer_prefix()))
1-element Vector{VarName{Symbol("inner.m"), typeof(identity)}}:
 inner.m
```

From this we can tell what the correct way to condition `m` within `demo_inner` is in the two different models.
