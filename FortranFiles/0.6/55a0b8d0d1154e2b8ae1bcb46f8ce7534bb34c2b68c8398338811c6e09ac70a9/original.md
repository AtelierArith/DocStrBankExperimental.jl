```
@fread f [ rec=N ] [ spec ... ]
```

Macro interface for reading data from the `FortranFile` `f`. A single `@fread` call will process a single data record from the file. Each `spec` can be:

  * a `var::T` declaration, which will read data of the type `T` from the file, and assign it to the variable `var`. `T` can be one of the usual Fortran scalar datatypes.
  * a `var::(T,dims...)` declaration, where `T` is a scalar datatype and `dims...` is a series of integers. This reads an array of the specified datatype and dimensions, and assigns it to the variable `var`.
  * `var::Array{T}(undef,dims...)` as an explicit form for reading arrays
  * a variable name, which must refer to a pre-allocated array.

Note that a `spec` can refer to variables assigned by previous specs. The `rec` keyword must be given iff `f` refers to a direct-access file, and specifies which record to read.

Example:

```
@fread f n::Int32 x::(Float64,n)
```

This reads a single `Int32`, assigns it to `n`, and then reads a `Float64` array with `n` elements and assigns it to `x`. Such a record can not be processed by the function-based `read` interface. The equivalent call would be

```
n, x = read(f, Int32, (Float64,n))
```

but this can't work because `n` is only assigned after the `read` statement is processed. The macro interface is provided to cover such cases.
