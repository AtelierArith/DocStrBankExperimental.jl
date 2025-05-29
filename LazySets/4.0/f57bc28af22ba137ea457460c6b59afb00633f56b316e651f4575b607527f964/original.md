# Extended help

```
area(X::LazySet)
```

### Notes

This algorithm is applicable to any polytopic set `X` whose list of vertices can be computed via `vertices_list`.

### Algorithm

Let `m` be the number of vertices of `X`. We consider the following instances:

  * `m = 0, 1, 2`: the output is zero.
  * `m = 3`: the triangle case is solved using the Shoelace formula with 3 points.
  * `m = 4`: the quadrilateral case is solved by the factored version of the          Shoelace formula with 4 points.

Otherwise, the general Shoelace formula is used; for details see the [Wikipedia page](https://en.wikipedia.org/wiki/Shoelace_formula).
