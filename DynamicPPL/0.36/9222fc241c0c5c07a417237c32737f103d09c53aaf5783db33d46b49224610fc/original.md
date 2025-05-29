```
values_as_in_model(model::Model, include_colon_eq::Bool, varinfo::AbstractVarInfo[, context::AbstractContext])
```

Get the values of `varinfo` as they would be seen in the model.

More specifically, this method attempts to extract the realization *as seen in the model*. For example, `x[1] ~ truncated(Normal(); lower=0)` will result in a realization that is compatible with `truncated(Normal(); lower=0)` – i.e. one where the value of `x[1]` is positive – regardless of whether `varinfo` is working in unconstrained space.

Hence this method is a "safe" way of obtaining realizations in constrained space at the cost of additional model evaluations.

# Arguments

  * `model::Model`: model to extract realizations from.
  * `include_colon_eq::Bool`: whether to also include variables on the LHS of `:=`.
  * `varinfo::AbstractVarInfo`: variable information to use for the extraction.
  * `context::AbstractContext`: base context to use for the extraction. Defaults  to `DynamicPPL.DefaultContext()`.

# Examples

## When `VarInfo` fails

The following demonstrates a common pitfall when working with [`VarInfo`](@ref) and constrained variables.

```jldoctest
julia> using Distributions, StableRNGs

julia> rng = StableRNG(42);

julia> @model function model_changing_support()
           x ~ Bernoulli(0.5)
           y ~ x == 1 ? Uniform(0, 1) : Uniform(11, 12)
       end;

julia> model = model_changing_support();

julia> # Construct initial type-stable `VarInfo`.
       varinfo = VarInfo(rng, model);

julia> # Link it so it works in unconstrained space.
       varinfo_linked = DynamicPPL.link(varinfo, model);

julia> # Perform computations in unconstrained space, e.g. changing the values of `θ`.
       # Flip `x` so we hit the other support of `y`.
       θ = [!varinfo[@varname(x)], rand(rng)];

julia> # Update the `VarInfo` with the new values.
       varinfo_linked = DynamicPPL.unflatten(varinfo_linked, θ);

julia> # Determine the expected support of `y`.
       lb, ub = θ[1] == 1 ? (0, 1) : (11, 12)
(0, 1)

julia> # Approach 1: Convert back to constrained space using `invlink` and extract.
       varinfo_invlinked = DynamicPPL.invlink(varinfo_linked, model);

julia> # (×) Fails! Because `VarInfo` _saves_ the original distributions
       # used in the very first model evaluation, hence the support of `y`
       # is not updated even though `x` has changed.
       lb ≤ first(varinfo_invlinked[@varname(y)]) ≤ ub
false

julia> # Approach 2: Extract realizations using `values_as_in_model`.
       # (✓) `values_as_in_model` will re-run the model and extract
       # the correct realization of `y` given the new values of `x`.
       lb ≤ values_as_in_model(model, true, varinfo_linked)[@varname(y)] ≤ ub
true
```
