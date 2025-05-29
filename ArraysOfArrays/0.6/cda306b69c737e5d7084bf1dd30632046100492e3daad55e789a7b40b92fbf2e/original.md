```
consgroupedview(source::AbstractVector, target)
```

Compute a grouping of equal consecutive elements on `source` via [`consgrouped_ptrs`](@ref) and apply the grouping to target, resp. each element of `target`. `target` may be an vector or a named or unnamed tuple of vectors. The result is a `VectorOfVectors`, resp. a tuple of such.

Example:

```
A = [1, 1, 2, 3, 3, 2, 2, 2]
B = [1, 2, 3, 4, 5, 6, 7, 8]
consgroupedview(A, B) == [[1, 2], [3], [4, 5], [6, 7, 8]]
```

`consgroupedview` plays well with columnar tables, too:

```julia
    using Tables, TypedTables
    data = Table(
        a = [1, 1, 2, 3, 3, 2, 2, 2],
        b = [1, 2, 3, 4, 5, 6, 7, 8],
        c = [1.1, 2.2, 3.3, 4.4, 5.5, 6.6, 7.7, 8.8]
    )

    result = Table(consgroupedview(data.a, Tables.columns(data)))
```

will return

```
     a          b          c
   ┌──────────────────────────────────────
 1 │ [1, 1]     [1, 2]     [1.1, 2.2]
 2 │ [2]        [3]        [3.3]
 3 │ [3, 3]     [4, 5]     [4.4, 5.5]
 4 │ [2, 2, 2]  [6, 7, 8]  [6.6, 7.7, 8.8]
```

without copying any data:

```
    flatview(result.a) === data.a
    flatview(result.b) === data.b
    flatview(result.c) === data.c
```
