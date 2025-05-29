```
AbstractVectorOfArray{T, N, A}
```

An AbstractVectorOfArray is an object which represents arrays of arrays, and arbitrary recursive nesting of arrays, as a single array-like object. Thus a canonical example of an AbstractVectorOfArray is something of the form `VectorOfArray([[1,2],[3,4]])`, which "acts" like the matrix [1 3; 2 4] where the data is stored and accessed in a column-ordered fashion (as is typical in Julia), but the actual matrix is never constructed and instead lazily represented through the type.

An AbstractVectorOfArray subtype should match the following behaviors.

!!! note
    In 2023 the linear indexing `A[i]``was deprecated. It previously had the behavior that`A[i] = A.u[i]`. However, this is incompatible with standard`AbstractArray`interfaces, Since if`A = VectorOfArray([[1,2],[3,4]])`and`A`is supposed to act like`[1 3; 2 4]`, then there is a difference`A[1] = [1,2]`for the VectorOfArray while`A[1] = 1`for the matrix. This causes many issues if`AbstractVectorOfArray <: AbstractArray`. Thus we plan in 2026 to complete the deprecation and thus have a breaking update where`A[i]`matches the linear indexing of an`AbstractArray`, and then making`AbstractVectorOfArray <: AbstractArray`. Until then,`AbstractVectorOfArray` due to this interface break but manaully implements an AbstractArray-like interface for future compatability.


## Fields

An AbstractVectorOfArray has the following fields:

  * `u` which holds the Vector of values at each timestep

## Array Interface

The general operations are as follows. Use

```julia
A.u[j]
```

to access the `j`th array. For multidimensional systems, this will address first by component and lastly by time, and thus

```julia
A[i, j]
```

will be the `i`th component at array `j`. Hence, `A[j][i] == A[i, j]`. This is done because Julia is column-major, so the leading dimension should be contiguous in memory. If the independent variables had shape (for example, was a matrix), then `i` is the linear index. We can also access solutions with shape:

```julia
A[i, k, j]
```

gives the `[i,k]` component of the system at array `j`. The colon operator is supported, meaning that

```julia
A[i, :]
```

gives the timeseries for the `i`th component.

## Using the AbstractArray Interface

The `AbstractArray` interface can be directly used. For example, for a vector system of variables `A[i,j]` is a matrix with rows being the variables and columns being the timepoints. Operations like `A'` will transpose the solution type. Functionality written for `AbstractArray`s can directly use this. For example, the Base `cov` function computes correlations amongst columns, and thus:

```julia
cov(A)
```

computes the correlation of the system state in time, whereas

```julia
cov(A, 2)
```

computes the correlation between the variables. Similarly, `mean(A,2)` is the mean of the variable in time, and `var(A,2)` is the variance. Other statistical functions and packages which work on `AbstractArray` types will work on the solution type.

## Conversions

At anytime, a true `Array` can be created using `Array(A)`, or more generally `stack(A)` to make the array type match the internal array type (for example, if `A` is an array of GPU arrays, `stack(A)` will be a GPU array).
