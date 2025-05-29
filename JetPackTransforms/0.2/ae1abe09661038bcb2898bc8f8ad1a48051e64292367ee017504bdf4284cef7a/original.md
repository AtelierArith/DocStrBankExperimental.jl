```
A = JopFft(T, n...[; dims=()])
```

where `A` is a Fourier transform, the domain of A is (T,n).  If `dims` is not set, then `A` is an N-dimensional Fourier transform and where `N=ndims(dom)`. Otherwise, `A` is a Fourier transform over the dimensions specifed by `dims`.

For a complex-to-complex transform: `range(A)::JetSpace`.  For a real-to-complex transform: `range(A)::JetSpaceSymmetric`.  Normally, JopFft is responsible for constructing range(A).  In the event that you need to manually construct this space, we provide a convenience method:

```
R = symspace(JopLn{JopFft_df!}, T, symdim, n...)
```

where `T` is the precision (generally `Float32` or `Float64`), `n...` is the dimensions of the domain of `A`, and `symdim` is the first dimension begin Fourier transformed.

# Examples

## 1D, real to complex

```julia
A = JopFft(Float64,128)
m = rand(domain(A))
d = A*m
```

## 1D, complex to complex

```julia
A = JopFft(ComplexF64,128)
m = rand(domain(A))
d = A*m
```

## 2D, real to complex

```julia
A = JopFft(Float64,128,256)
m = rand(domain(A))
d = A*m
```

## 3D, real to complex, transforming over only the first dimension

```julia
A = JopFft(Float64,128,256; dims=(1,))
m = rand(domain(A))
d = A*m
```
