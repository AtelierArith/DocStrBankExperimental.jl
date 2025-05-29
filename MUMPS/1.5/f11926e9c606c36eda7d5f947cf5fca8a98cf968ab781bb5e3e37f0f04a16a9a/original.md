```
associate_rhs!(mumps, rhs; unsafe=false)
```

Register a dense or sparse RHS matrix or vector `rhs` to a `mumps` object. It internally converts `rhs` to be consistent with the ICNTL[20] setting, and additionally allocates `mumps.rhs` according to the ICNTL[21] setting.

If needed, it tries to convert element type of `rhs` to be consistent with type of `mumps`, throwing a warning in this case.

Note that this function makes a copy of `rhs`. If you do not want to make a copy, pass `unsafe=false`. If the type of `rhs` needs to be converted, this function may copy `rhs` twice - to avoid this use `unsafe=false`.

When `unsafe=false` is passed, if the type of `rhs` is already consistent with the type of `mumps`, then pointers to `rhs`'s memory are passed directly to MUMPS, so modifying `rhs` will modify the rhs in `mumps`.  If `rhs` is not already consistent, a copy will be made when the type is converted.

See also: [`associate_matrix!`](@ref)
