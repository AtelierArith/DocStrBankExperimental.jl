```julia
check_unitary(𝐔; rtol, atol)

```

Test if `𝐔` is a unitary matrix. The function checks how close both $𝐔𝐔^†$ and $𝐔^†𝐔$ are to $I$, with relative and absolute error given by `rtol`, `atol`.

# Examples

```julia-repl
julia> check_unitary(exp(-1.0im*5*0.5*σx))
true
```
