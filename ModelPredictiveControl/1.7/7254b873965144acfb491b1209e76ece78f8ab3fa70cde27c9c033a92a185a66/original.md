```
default_nint(model::LinModel, i_ym=1:model.ny, nint_u=0) -> nint_ym
```

Get default integrator quantity per measured outputs `nint_ym` for [`LinModel`](@ref).

The arguments `i_ym` and `nint_u` are the measured output indices and the integrator quantity on each manipulated input, respectively. By default, one integrator is added on each measured outputs. If $\mathbf{Â, Ĉ}$ matrices of the augmented model become unobservable, the integrator is removed. This approach works well for stable, integrating and unstable `model` (see Examples).

# Examples

```jldoctest
julia> model = LinModel(append(tf(3, [10, 1]), tf(2, [1, 0]), tf(4,[-5, 1])), 1.0);

julia> nint_ym = default_nint(model)
3-element Vector{Int64}:
 1
 0
 1
```
