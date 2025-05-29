```
 ppeval(f, D...; dim::NTuple)
```

Evaluates the callable argument `f` on slices of the elements of the `D` tuple.

#### Arguments

`f` can be any callable object that accepts sliced or broadcasted elements of `D`. The result returned from `f` must be either an array or a scalar.

`D` has any number of elements and the elements can have any type. If an element of `D` is a distributed array along the dimension specified by `dim`. If an element of `D` is not distributed, the element is by default broadcasted and applied on all evaluations of `f`.

`dim` is a tuple of integers specifying the dimension over which the elements of `D` is slices. The length of the tuple must therefore be the same as the number of arguments `D`. By default distributed arrays are slides along the last dimension. If the value is less than or equal to zero the element are broadcasted to all evaluations of `f`.

#### Result

`ppeval` returns a distributed array of dimension `p+1` where the first `p` sizes correspond to the sizes of return values of `f`. The last dimension of the return array from `ppeval` has the same length as the dimension over which the input arrays are sliced.

#### Examples

```jl
addprocs(Sys.CPU_THREADS)

using DistributedArrays

A = drandn((10, 10, Sys.CPU_THREADS), workers(), [1, 1, Sys.CPU_THREADS])

ppeval(eigvals, A)

ppeval(eigvals, A, randn(10,10)) # broadcasting second argument

B = drandn((10, Sys.CPU_THREADS), workers(), [1, Sys.CPU_THREADS])

ppeval(*, A, B)
```
