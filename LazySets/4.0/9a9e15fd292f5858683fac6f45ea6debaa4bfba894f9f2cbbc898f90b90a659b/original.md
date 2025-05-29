```
isflat(H::AbstractHyperrectangle)
```

Check whether a hyperrectangular set is flat, i.e., whether its radius is zero in some dimension.

### Input

  * `H` – hyperrectangular set

### Output

`true` iff the hyperrectangular set is flat.

### Notes

For robustness with respect to floating-point inputs, this function relies on the result of `isapproxzero` when applied to the radius in some dimension. Hence this function depends on the absolute zero tolerance `ABSZTOL`.
