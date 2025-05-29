```
Divisors{T}
```

An iterator for the divisors of a given object. Create using     `Divisors(A, power::Int = 1)` where $A$ is either a FacElem or a direct element. Power can be used to restrict to objects $B$ s.th. $B$^power still divides $A$, e.g.     `Divisors(12, powers = 2)` will produce square divisors.

For rings where this makes sense, i.e. where the unit group is finite, `units = true` can be passed in to also take into account the units.
