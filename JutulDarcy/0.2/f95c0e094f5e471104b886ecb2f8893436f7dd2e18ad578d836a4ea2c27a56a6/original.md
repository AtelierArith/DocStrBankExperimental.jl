```
mask = PerforationMask(mask::Vector)
```

Create a perforation mask. This can be passed to [`setup_forces`](@ref) for a well under the `mask` argument. The mask should equal the number of perforations in the well and is applied to the reference well indices in a multiplicative fashion. For example, if a well named `:Injector` has two perforations, the following mask would disable the first perforation and decrease the connection strength for the second perforation by 50%:

```julia
mask = PerforationMask([0.0, 0.5])
iforces = setup_forces(W, mask = mask)
forces = setup_reservoir_forces(model, control = controls, Injector = iforces)
```
