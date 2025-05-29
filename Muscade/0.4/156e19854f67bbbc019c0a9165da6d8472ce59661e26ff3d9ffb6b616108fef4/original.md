```
ilast = findlastassigned(state)
```

Find the index `ilast` of the element before the first non assigment element in a vector `state`.

In multistep analyses, `solve` returns a vector `state` of length equal to the number of steps requested by the user.  If the analysis is aborted, `solve` still returns any available results at the begining of `state`, and the vector `state[1:ilast]` is fully assigned.

See also: [`solve`](@ref)
