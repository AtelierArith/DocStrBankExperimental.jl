```
fix(model::Model; values...)
fix(model::Model, values::NamedTuple)
```

Return a `Model` which now treats the variables in `values` as fixed.

See also: [`unfix`](@ref), [`fixed`](@ref)

# Examples

## Simple univariate model

```jldoctest fix
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
       fixed_model = fix(model, x=100.0, m=1.0);

julia> m, x = fixed_model(); (m == 1.0 && x == 100.0)
true

julia> # Let's only fix on `x = 100.0`.
       fixed_model = fix(model, x = 100.0);

julia> m, x = fixed_model(); (m ≠ 1.0 && x == 100.0)
true
```

The above uses a `NamedTuple` to hold the fixed variables, which allows us to perform some additional optimizations; in many cases, the above has zero runtime-overhead.

But we can also use a `Dict`, which offers more flexibility in the fixing (see examples further below) but generally has worse performance than the `NamedTuple` approach:

```jldoctest fix
julia> fixed_model_dict = fix(model, Dict(@varname(x) => 100.0));

julia> m, x = fixed_model_dict(); (m ≠ 1.0 && x == 100.0)
true

julia> # Alternative: pass `Pair{<:VarName}` as positional argument.
       fixed_model_dict = fix(model, @varname(x) => 100.0, );

julia> m, x = fixed_model_dict(); (m ≠ 1.0 && x == 100.0)
true
```

## Fix only a part of a multivariate variable

We can not only fix multivariate random variables, but we can also use the standard mechanism of setting something to `missing` in the call to `fix` to only fix a part of the variable.

```jldoctest fix
julia> @model function demo_mv(::Type{TV}=Float64) where {TV}
           m = Vector{TV}(undef, 2)
           m[1] ~ Normal()
           m[2] ~ Normal()
           return m
       end
demo_mv (generic function with 4 methods)

julia> model = demo_mv();

julia> fixed_model = fix(model, m = [missing, 1.0]);

julia> # (✓) `m[1]` sampled while `m[2]` is fixed
       m = fixed_model(); (m[1] ≠ 1.0 && m[2] == 1.0)
true
```

Intuitively one might also expect to be able to write something like `fix(model, var"m[1]" = 1.0, )`. Unfortunately this is not supported as it has the potential of increasing compilation times but without offering any benefit with respect to runtime:

```jldoctest fix
julia> # (×) `m[2]` is not set to 1.0.
       m = fix(model, var"m[2]" = 1.0)(); m[2] == 1.0
false
```

But you *can* do this if you use a `Dict` as the underlying storage instead:

```jldoctest fix
julia> # Alternative: `fix(model, Dict(@varname(m[2] => 1.0)))`
       # (✓) `m[2]` is set to 1.0.
       m = fix(model, @varname(m[2]) => 1.0)(); (m[1] ≠ 1.0 && m[2] == 1.0)
true
```

## Nested models

`fix` of course also supports the use of nested models through the use of [`to_submodel`](@ref), similar to [`condition`](@ref).

```jldoctest fix
julia> @model demo_inner() = m ~ Normal()
demo_inner (generic function with 2 methods)

julia> @model function demo_outer()
           inner ~ to_submodel(demo_inner())
           return inner
       end
demo_outer (generic function with 2 methods)

julia> model = demo_outer();

julia> model() ≠ 1.0
true

julia> fixed_model = fix(model, (@varname(inner.m) => 1.0, ));

julia> fixed_model()
1.0
```

However, unlike [`condition`](@ref), `fix` can also be used to fix the return-value of the submodel:

```julia
julia> fixed_model = fix(model, inner = 2.0,);

julia> fixed_model()
2.0
```

## Difference from `condition`

A very similar functionality is also provided by [`condition`](@ref). The only difference between fixing and conditioning is as follows:

  * `condition`ed variables are considered to be observations, and are thus included in the computation [`logjoint`](@ref) and [`loglikelihood`](@ref), but not in [`logprior`](@ref).
  * `fix`ed variables are considered to be constant, and are thus not included in any log-probability computations.

```juliadoctest fix
julia> @model function demo()
           m ~ Normal()
           x ~ Normal(m, 1)
           return (; m=m, x=x)
       end
demo (generic function with 2 methods)

julia> model = demo();

julia> model_fixed = fix(model, m = 1.0);

julia> model_conditioned = condition(model, m = 1.0);

julia> logjoint(model_fixed, (x=1.0,))
-0.9189385332046728

julia> # Different!
       logjoint(model_conditioned, (x=1.0,))
-2.3378770664093453

julia> # And the difference is the missing log-probability of `m`:
       logjoint(model_fixed, (x=1.0,)) + logpdf(Normal(), 1.0) == logjoint(model_conditioned, (x=1.0,))
true
```
