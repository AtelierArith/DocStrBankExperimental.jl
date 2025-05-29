```julia
struct SimpleVarInfo{NT, T, C<:DynamicPPL.AbstractTransformation} <: DynamicPPL.AbstractVarInfo
```

A simple wrapper of the parameters with a `logp` field for accumulation of the logdensity.

Currently only implemented for `NT<:NamedTuple` and `NT<:AbstractDict`.

# Fields

  * `values`: underlying representation of the realization represented
  * `logp`: holds the accumulated log-probability
  * `transformation`: represents whether it assumes variables to be transformed

# Notes

The major differences between this and `NTVarInfo` are:

1. `SimpleVarInfo` does not require linearization.
2. `SimpleVarInfo` can use more efficient bijectors.
3. `SimpleVarInfo` is only type-stable if `NT<:NamedTuple` and either a) no indexing is used in tilde-statements, or b) the values have been specified with the correct shapes.

# Examples

## General usage

```jldoctest simplevarinfo-general; setup=:(using Distributions)
julia> using StableRNGs

julia> @model function demo()
           m ~ Normal()
           x = Vector{Float64}(undef, 2)
           for i in eachindex(x)
               x[i] ~ Normal()
           end
           return x
       end
demo (generic function with 2 methods)

julia> m = demo();

julia> rng = StableRNG(42);

julia> ### Sampling ###
       ctx = SamplingContext(rng, SampleFromPrior(), DefaultContext());

julia> # In the `NamedTuple` version we need to provide the place-holder values for
       # the variables which are using "containers", e.g. `Array`.
       # In this case, this means that we need to specify `x` but not `m`.
       _, vi = DynamicPPL.evaluate!!(m, SimpleVarInfo((x = ones(2), )), ctx);

julia> # (✓) Vroom, vroom! FAST!!!
       vi[@varname(x[1])]
0.4471218424633827

julia> # We can also access arbitrary varnames pointing to `x`, e.g.
       vi[@varname(x)]
2-element Vector{Float64}:
 0.4471218424633827
 1.3736306979834252

julia> vi[@varname(x[1:2])]
2-element Vector{Float64}:
 0.4471218424633827
 1.3736306979834252

julia> # (×) If we don't provide the container...
       _, vi = DynamicPPL.evaluate!!(m, SimpleVarInfo(), ctx); vi
ERROR: type NamedTuple has no field x
[...]

julia> # If one does not know the varnames, we can use a `OrderedDict` instead.
       _, vi = DynamicPPL.evaluate!!(m, SimpleVarInfo{Float64}(OrderedDict()), ctx);

julia> # (✓) Sort of fast, but only possible at runtime.
       vi[@varname(x[1])]
-1.019202452456547

julia> # In addtion, we can only access varnames as they appear in the model!
       vi[@varname(x)]
ERROR: KeyError: key x not found
[...]

julia> vi[@varname(x[1:2])]
ERROR: KeyError: key x[1:2] not found
[...]
```

*Technically*, it's possible to use any implementation of `AbstractDict` in place of `OrderedDict`, but `OrderedDict` ensures that certain operations, e.g. linearization/flattening of the values in the varinfo, are consistent between evaluations. Hence `OrderedDict` is the preferred implementation of `AbstractDict` to use here.

You can also sample in *transformed* space:

```jldoctest simplevarinfo-general
julia> @model demo_constrained() = x ~ Exponential()
demo_constrained (generic function with 2 methods)

julia> m = demo_constrained();

julia> _, vi = DynamicPPL.evaluate!!(m, SimpleVarInfo(), ctx);

julia> vi[@varname(x)] # (✓) 0 ≤ x < ∞
1.8632965762164932

julia> _, vi = DynamicPPL.evaluate!!(m, DynamicPPL.settrans!!(SimpleVarInfo(), true), ctx);

julia> vi[@varname(x)] # (✓) -∞ < x < ∞
-0.21080155351918753

julia> xs = [last(DynamicPPL.evaluate!!(m, DynamicPPL.settrans!!(SimpleVarInfo(), true), ctx))[@varname(x)] for i = 1:10];

julia> any(xs .< 0)  # (✓) Positive probability mass on negative numbers!
true

julia> # And with `OrderedDict` of course!
       _, vi = DynamicPPL.evaluate!!(m, DynamicPPL.settrans!!(SimpleVarInfo(OrderedDict()), true), ctx);

julia> vi[@varname(x)] # (✓) -∞ < x < ∞
0.6225185067787314

julia> xs = [last(DynamicPPL.evaluate!!(m, DynamicPPL.settrans!!(SimpleVarInfo(), true), ctx))[@varname(x)] for i = 1:10];

julia> any(xs .< 0) # (✓) Positive probability mass on negative numbers!
true
```

Evaluation in transformed space of course also works:

```jldoctest simplevarinfo-general
julia> vi = DynamicPPL.settrans!!(SimpleVarInfo((x = -1.0,)), true)
Transformed SimpleVarInfo((x = -1.0,), 0.0)

julia> # (✓) Positive probability mass on negative numbers!
       getlogp(last(DynamicPPL.evaluate!!(m, vi, DynamicPPL.DefaultContext())))
-1.3678794411714423

julia> # While if we forget to indicate that it's transformed:
       vi = DynamicPPL.settrans!!(SimpleVarInfo((x = -1.0,)), false)
SimpleVarInfo((x = -1.0,), 0.0)

julia> # (✓) No probability mass on negative numbers!
       getlogp(last(DynamicPPL.evaluate!!(m, vi, DynamicPPL.DefaultContext())))
-Inf
```

## Indexing

Using `NamedTuple` as underlying storage.

```jldoctest
julia> svi_nt = SimpleVarInfo((m = (a = [1.0], ), ));

julia> svi_nt[@varname(m)]
(a = [1.0],)

julia> svi_nt[@varname(m.a)]
1-element Vector{Float64}:
 1.0

julia> svi_nt[@varname(m.a[1])]
1.0

julia> svi_nt[@varname(m.a[2])]
ERROR: BoundsError: attempt to access 1-element Vector{Float64} at index [2]
[...]

julia> svi_nt[@varname(m.b)]
ERROR: type NamedTuple has no field b
[...]
```

Using `OrderedDict` as underlying storage.

```jldoctest
julia> svi_dict = SimpleVarInfo(OrderedDict(@varname(m) => (a = [1.0], )));

julia> svi_dict[@varname(m)]
(a = [1.0],)

julia> svi_dict[@varname(m.a)]
1-element Vector{Float64}:
 1.0

julia> svi_dict[@varname(m.a[1])]
1.0

julia> svi_dict[@varname(m.a[2])]
ERROR: BoundsError: attempt to access 1-element Vector{Float64} at index [2]
[...]

julia> svi_dict[@varname(m.b)]
ERROR: type NamedTuple has no field b
[...]
```
