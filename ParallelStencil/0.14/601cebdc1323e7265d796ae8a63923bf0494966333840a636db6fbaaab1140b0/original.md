```
@CellType(name, <keyword arguments>)
```

Create a cell type, which can then be passed to `@zeros`, `@ones`, `@rand`, `@falses`, `@trues` or `@fill` using the keyword argument `celltype`.

!!! note "Advanced"
    The element type `eltype` can be explicitly passed as keyword argument in order to be used instead of the default `numbertype` chosen with [`@init_parallel_stencil`](@ref). If no default `numbertype` was chosen [`@init_parallel_stencil`](@ref), then the keyword argument `eltype` is mandatory, except if `parametric=true` is set. This needs to be used with care to ensure that no datatype conversions occur in performance critical computations.


# Arguments

  * `name`: the name of the cell type.

# Keyword arguments

  * `eltype::DataType`: the type of the elements, which can be numbers, indices, booleans or enums.
  * `fieldnames::String|NTuple{N,String}`: the names of the fields of the cell. Note that cell values can always be addressed with array indices, even when field names are defined.
  * `dims::Integer|NTuple{N,Integer}=length(fieldnames)`: the dimensions of the cell. A cell can contain a single value or an N-dimensional array of the specified dimensions. A valid dims argument must fullfill `prod(dims)==length(fieldnames)`. If `dims` is omitted, then it will be automatically set as `dims=length(fieldnames)`, defining the cell to contain a 1-D array of appropriate length.

!!! note "Advanced"
      * `parametric::Bool=false`: whether the cell type has a fixed or parametrisable element type. If `parametric=true` is set, then the keyword argument `eltype` is invalid.


# Examples

```
@CellType SymmetricTensor2D fieldnames=(xx, zz, xz)
#(...)
A = @zeros(nx, ny, celltype=SymmetricTensor2D)

@CellType SymmetricTensor3D fieldnames=(xx, yy, zz, yz, xz, xy)
#(...)
A = @zeros(nx, ny, nz, celltype=SymmetricTensor3D)

@CellType Tensor2D fieldnames=(xxxx, yxxx, xyxx, yyxx, xxyx, yxyx, xyyx, yyyx, xxxy, yxxy, xyxy, yyxy, xxyy, yxyy, xyyy, yyyy) dims=(2,2,2,2)
#(...)
A = @zeros(nx, ny, celltype=Tensor2D)

@CellType SymmetricTensor2D fieldnames=(xx, zz, xz) parametric=true
#(...)
A = @zeros(nx, ny, celltype=SymmetricTensor2D{Float32})

@CellType SymmetricTensor2D fieldnames=(xx, zz, xz) eltype=Float32
#(...)
A = @zeros(nx, ny, celltype=SymmetricTensor2D)
```

See also: [`@zeros`](@ref), [`@ones`](@ref), [`@rand`](@ref), [`@falses`](@ref), [`@trues`](@ref), [`@fill`](@ref)
