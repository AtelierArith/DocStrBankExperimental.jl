```julia
resetInitialValues!(dest; ...)
resetInitialValues!(dest, src; ...)
resetInitialValues!(dest, src, initKey; ...)
resetInitialValues!(dest, src, initKey, solveKey; varList)

```

Set solveKey values of `dest::AbstractDFG` according to `initKey::Symbol=:graphinit` values.

Notes

  * Some flexibility for using two DFGs and different key values, see Examples and code for details.
  * Can also be specific with `varList::Vector{Symbol}`.
  * Returns `dest` graph.
  * Uses the supersolve mechanism.

Examples

```julia
resetInitialValues!(fg)
resetInitialValues!(fg1,fg2)  # into 1 from 2
resetInitialValues!(fg1,fg1,:myotherinit)  # use different init value into solveKey :default
resetInitialValues!(fg1,fg1,:graphinit, :mysolver) # not into solveKey=:default but :mysolver
resetInitialValues!(fg1, varList=[:x1;:l3])  # Specific variables only

# Into `fgNew` object, leaving `fg` untouched
fgNew = deepcopy(fg)
resetInitialValues!(fgNew,fg)
```

Related

initVariable!, graphinit (keyword)
