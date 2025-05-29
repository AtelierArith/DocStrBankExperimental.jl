```
associate_matrix!(mumps,A; unsafe=false)
```

Register the square matrix `A` to a `mumps` object. It internally converts `A` to be consistent with the ICNTL[5] setting.

If needed, it tries to convert element type of `A` to be consistent with type of `mumps`, throwing a warning in this case.

Note that by default this function makes a copy of `A`. If you do not want to make a copy, pass `unsafe=true`. If the type of `A` needs to be converted, this function may copy `A` twice - to avoid this use `unsafe=true`.

When `unsafe=true` is passed, if the type of `A` is already consistent with the type of `mumps`, then pointers to `A`'s memory are passed directly to MUMPS, so modifying `A` will modify the matrix in `mumps`.  If `A` is not already consistent, a copy will be made when the type is converted. Warning: A dense, symmetric matrix will always be copied when it is converted to MUMPS's internal representation.

See also: [`associate_rhs!`](@ref)
