```
deactivate_overwritten_control_points!(
    control_points::LocallyRefinedControlPoints,
    local_refinement_level::Integer)::Nothing
```

Deactivate control points whose effect is completely overwritten. The procedure works as follows:

The 'forward' computation to process local refinement is as follows:

`B = (O₂ ∘ L ∘ O₁)(A)`,

where:

  * `A` is the control point grid at `local_refinement_level`
  * `B` is the control point grid at `local_refinement_level + 1`
  * `O₁` is the overwriting operation of the active control points at `local_refinement_level`
  * `L` is the linear operation consisting of multiplying by refinement matrices along specified dimensions
  * `O₂` is the overwriting operation of the active control points at `local_refinement_level + 1`

To figure out whether for any overwriting element of `O₁` its effect is still present in the final array, we perform the following computation:

`A = (L* ∘ O₂)(B)`,

where:

  * `B` is initialized with a special number `Flag`, which is a simple wrapper of a Boolean effectively saying whether this number is relevant or not. `B` is initialized with all `Flag(true)`
  * The overwriting values of `O₂` are initialized with all `Flag(false)`
  * `L*` is the adjoint version of `L`

After this computation we can read of in `A` at the overwriting locations of `O₁` whether each number is still having an effect on `B` or not.
