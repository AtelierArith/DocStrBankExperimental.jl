```
@submodel prefix=... model
@submodel prefix=... ... = model
```

Run a Turing `model` nested inside of a Turing model and add "`prefix`." as a prefix to all random variables inside of the `model`.

Valid expressions for `prefix=...` are:

  * `prefix=false`: no prefix is used.
  * `prefix=true`: *attempt* to automatically determine the prefix from the left-hand side `... = model` by first converting into a `VarName`, and then calling `Symbol` on this.
  * `prefix=expression`: results in the prefix `Symbol(expression)`.

The prefix makes it possible to run the same Turing model multiple times while keeping track of all random variables correctly.

# Examples

## Example models

```jldoctest submodelprefix; setup=:(using Distributions)
julia> @model function demo1(x)
           x ~ Normal()
           return 1 + abs(x)
       end;

julia> @model function demo2(x, y, z)
            @submodel prefix="sub1" a = demo1(x)
            @submodel prefix="sub2" b = demo1(y)
            return z ~ Uniform(-a, b)
       end;
```

When we sample from the model `demo2(missing, missing, 0.4)` random variables `sub1.x` and `sub2.x` will be sampled:

```jldoctest submodelprefix
julia> vi = VarInfo(demo2(missing, missing, 0.4));

julia> @varname(var"sub1.x") in keys(vi)
true

julia> @varname(var"sub2.x") in keys(vi)
true
```

Variables `a` and `b` are not tracked since they can be computed from the random variables `sub1.x` and `sub2.x` that were tracked when running `demo1`:

```jldoctest submodelprefix
julia> @varname(a) in keys(vi)
false

julia> @varname(b) in keys(vi)
false
```

We can check that the log joint probability of the model accumulated in `vi` is correct:

```jldoctest submodelprefix
julia> sub1_x = vi[@varname(var"sub1.x")];

julia> sub2_x = vi[@varname(var"sub2.x")];

julia> logprior = logpdf(Normal(), sub1_x) + logpdf(Normal(), sub2_x);

julia> loglikelihood = logpdf(Uniform(-1 - abs(sub1_x), 1 + abs(sub2_x)), 0.4);

julia> getlogp(vi) ≈ logprior + loglikelihood
true
```

## Different ways of setting the prefix

```jldoctest submodel-prefix-alternatives; setup=:(using DynamicPPL, Distributions)
julia> @model inner() = x ~ Normal()
inner (generic function with 2 methods)

julia> # When `prefix` is unspecified, no prefix is used.
       @model submodel_noprefix() = @submodel a = inner()
submodel_noprefix (generic function with 2 methods)

julia> @varname(x) in keys(VarInfo(submodel_noprefix()))
true

julia> # Explicitely don't use any prefix.
       @model submodel_prefix_false() = @submodel prefix=false a = inner()
submodel_prefix_false (generic function with 2 methods)

julia> @varname(x) in keys(VarInfo(submodel_prefix_false()))
true

julia> # Automatically determined from `a`.
       @model submodel_prefix_true() = @submodel prefix=true a = inner()
submodel_prefix_true (generic function with 2 methods)

julia> @varname(var"a.x") in keys(VarInfo(submodel_prefix_true()))
true

julia> # Using a static string.
       @model submodel_prefix_string() = @submodel prefix="my prefix" a = inner()
submodel_prefix_string (generic function with 2 methods)

julia> @varname(var"my prefix.x") in keys(VarInfo(submodel_prefix_string()))
true

julia> # Using string interpolation.
       @model submodel_prefix_interpolation() = @submodel prefix="$(nameof(inner()))" a = inner()
submodel_prefix_interpolation (generic function with 2 methods)

julia> @varname(var"inner.x") in keys(VarInfo(submodel_prefix_interpolation()))
true

julia> # Or using some arbitrary expression.
       @model submodel_prefix_expr() = @submodel prefix=1 + 2 a = inner()
submodel_prefix_expr (generic function with 2 methods)

julia> @varname(var"3.x") in keys(VarInfo(submodel_prefix_expr()))
true

julia> # (×) Automatic prefixing without a left-hand side expression does not work!
       @model submodel_prefix_error() = @submodel prefix=true inner()
ERROR: LoadError: cannot automatically prefix with no left-hand side
[...]
```

# Notes

  * The choice `prefix=expression` means that the prefixing will incur a runtime cost. This is also the case for `prefix=true`, depending on whether the expression on the the right-hand side of `... = model` requires runtime-information or not, e.g. `x = model` will result in the *static* prefix `x`, while `x[i] = model` will be resolved at runtime.
