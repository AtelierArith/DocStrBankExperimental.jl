```
set_coherent!(sys::System, Z, site::Site)
```

Set a coherent spin state at a [`Site`](@ref) using the $N$ complex amplitudes in `Z`.

For a single quantum spin-$s$, these amplitudes will be interpreted in the eigenbasis of $Ŝ^z$. That is, `Z[1]` represents the amplitude for the basis state fully polarized along the $ẑ$-direction, and subsequent components represent states with decreasing angular momentum along this axis ($m = s, s-1, …, -s$).
