```
newton = NewtonFlash()
newton = NewtonFlash(dMax = 0.2)
```

Flash using Newton's method for zero solve. Only conditionally convergent, but has better convergence rate than SSI.

# Arguments

  * `dMax`: dampening factor for the newton iteration

See also: [`flash_2ph!`](@ref), [`SSIFlash`](@ref) [`SSINewtonFlash`](@ref)
