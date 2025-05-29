```
nest([A1, A2, ...])
nest([A1, A2, ...], sym)
```

Creates an array with `ndims(A1)+1` dimensions. All the constituent arrays should be similar! Optional 2nd argument names the new dimension, giving `DimArray(nest(...),sym)`; this also happens if `A1 isa DimArray`.

```
[A1, A2, ...] |> nest(s)
```

Gives a function which acts on vectors as above.
