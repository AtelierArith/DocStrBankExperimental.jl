```
find_dstrain!(material::AbstractMaterial, dstrain::AbstractVector{<:Real},
              dt::Real, update_dstrain!::Function;
              max_iter::Integer=50, tol::Real=1e-9)
```

Find a compatible strain increment for `material`.

Chances are you'll only need to call this low-level function directly if you want to implement new kinds of strain optimizers. See `general_increment!` and `stress_driven_general_increment!` for usage examples.

This is the skeleton of the optimizer. The individual specific optimizer functions (`update_dstrain!)` only need to define how to update `dstrain`. The skeleton itself isn't a Newton-Raphson root finder. It just abstracts away the iteration loop, convergence checking and data plumbing, so it can be used, among other kinds, to conveniently implement Newton-Raphson root finders.

The `dstrain` supplied to this function is the initial guess for the optimization. At each iteration, it must be updated by the user-defined corrector `update_dstrain!`, whose call signature is:

```
update_dstrain!(dstrain::V, dstress::V, jacobian::AbstractArray{T})
    where V <: AbstractVector{T} where T <: Real
  -> err::Real
```

`dstrain` is the current value of the strain increment, in Voigt format. Conversion to tensor format uses `offdiagscale=2.0`. The function must update the Voigt format `dstrain` in-place.

`dstress = stress - stress0`, where `stress` is the stress state predicted by integrating the material for one timestep of length `dt`, using the current value of `dstrain` as a driving strain increment, and `stress0` is the stress state stored in `materials.variables.stress`.

`jacobian` is ∂σij/∂εkl (`material.variables_new.jacobian`), as computed by the material implementation. In many cases, the dstrain optimization can actually be performed by a Newton-Raphson root finder, so we pass the jacobian to facilitate writing the update formula for such a root finder.

The return value `err` must be an error measure (Real, >= 0).

The update is iterated at most `max_iter` times, until `err` falls below `tol`.

If `max_iter` is reached and the error measure is still `tol` or greater, `ErrorException` is thrown.

To keep features orthogonal, the timestep is **not** committed automatically. We call `integrate_material!`, but not `update_material!`. In other words, we only update `material.variables_new`. To commit the timestep, call `update_material!` after the optimizer is done.
