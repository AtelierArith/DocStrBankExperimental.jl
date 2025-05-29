```
place(A, B, p, opt=:c; direct = false)
place(sys::StateSpace, p, opt=:c; direct = false)
```

Calculate the gain matrix `K` such that `A - BK` has eigenvalues `p`.

```
place(A, C, p, opt=:o)
place(sys::StateSpace, p, opt=:o)
```

Calculate the observer gain matrix `L` such that `A - LC` has eigenvalues `p`.

If `direct = true` and `opt = :o`, the the observer gain `K` is calculated such that `A - KCA` has eigenvalues `p`, this option is to be used together with `direct = true` in [`observer_controller`](@ref). 

Note: only apply `direct = true` to discrete-time systems.

Ref: "Computer-Controlled Systems" pp 140.

Uses Ackermann's formula for SISO systems and [`place_knvd`](@ref) for MIMO systems. 

Please note that this function can be numerically sensitive, solving the placement problem in extended precision might be beneficial.
