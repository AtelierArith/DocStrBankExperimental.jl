```
DataCache{D, F<:Function}
```

Type for caching data, such as vectors, matrices, and numbers.

`D` = type of the data, for instance `Matrix{Float64}` or `Float32`. `F` = type of the function to update the entries of the array.

Signature of the function to fill the cache with the value of the array is as follows:

```
function fillcache!(cacheout::D,
    XYZ::AbstractVecOrMat{<:Real}, tangents::AbstractMatrix{<:Real},
    feid::IT, qpid::IT) where {D, T, IT}
    ... # modify the value of cacheout
    return cacheout
end
```

It may use the location `XYZ`, it may use the columns of the Jacobian matrix of the element, `tangents`, it may also choose the value of the finite element identifier (i.e. serial number), `feid`, and the identifier (i.e. serial number) of the quadrature point, `qpid`. All of these values are supplied by the code requesting the value of the cache. It must return the modified argument `cacheout`.

When the cache is accessed, the callback `fillcache!` is called, and the output `cacheout` is filled with the value of the cached data.

# Example

```
function fillcache!(cacheout::Array{CT, N},
        XYZ::AbstractVecOrMat{<:Real}, tangents::AbstractMatrix{<:Real},
        feid::IT, qpid::IT) where {CT, N, T, IT}
    cacheout .= LinearAlgebra.I(3)
    return cacheout
end
c = DataCache(zeros(Float32, 3, 3), fillcache!)
function f(c)
    XYZ, tangents, feid, qpid = (reshape([0.0, 0.0], 1, 2), [1.0 0.0; 0.0 1.0], 1, 1)
    data = c(XYZ, tangents, feid, qpid)
end
@test f(c) == LinearAlgebra.I(3)
```

!!! note
    The point of the data cache is that there will be no copying of data. The cache data field is filled in and returned, but no data needs to be copied. The bad news is, the cache is not thread safe. Reading is okay, but writing can lead to data races.

