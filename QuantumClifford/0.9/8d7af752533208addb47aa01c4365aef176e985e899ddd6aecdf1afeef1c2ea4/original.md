Return the given stabilizer without all the qubits in the given iterable.

The resulting tableaux is not guaranteed to be valid (to retain its commutation relationships).

```jldoctest
julia> delete_columns(S"XYZ YZX ZXY", [1,3])
+ Y
+ Z
+ X
```

See also: [`traceout!`](@ref)
