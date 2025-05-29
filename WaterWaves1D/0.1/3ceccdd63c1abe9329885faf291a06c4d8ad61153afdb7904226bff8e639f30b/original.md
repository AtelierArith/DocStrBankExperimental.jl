```
Init(data ; fast, label)
```

Generate an initial data to be used in the function `Problem`.

`data` should contain either

  * a function `η` and a function `v` (in this order);
  * a `mesh` (of type `Mesh`) and two vectors representing `η(mesh.x)` and `v(mesh.x)` (in this order);
  * an array of collocation points and two vectors representing `η(x)` and `v(x)` (in this order).

In the last two cases, an optional keyword argument `fast` can be set to `true`, (default is `false`), in which case the algorithm is faster and uses less allocations, but is less precise.

In the last case, the collocation points must be regularly spaced, otherwise an `ErrorException` is raised.

If the keyword `label::String` (used to display information to the output stream) is not provided, then it is set to the `"user-defined"`.
