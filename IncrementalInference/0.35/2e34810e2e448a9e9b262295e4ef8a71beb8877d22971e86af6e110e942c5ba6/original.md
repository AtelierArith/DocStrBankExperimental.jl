```julia
deconvSolveKey(dfg, refSym, refKey, tstSym, tstKey; tfg)

```

Calculate the relative difference between two variables and across solveKeys.

Example

```julia
fg = generateGraph_Kaess()
solveTree!(fg, storeOld=true)
# calculate the relative motion induced by the solver from init to solve.
pts = deconvSolveKey(fg, :x1, :default, :x1, :graphinit)
```

Notes

  * Can pass user `tfg::AbstractDFG` for better in-place operations.

DevNotes

  * TODO use dfg, rather than building new tfg internally.

Related

[`approxDeconv`](@ref), [`mmd`](@ref)
