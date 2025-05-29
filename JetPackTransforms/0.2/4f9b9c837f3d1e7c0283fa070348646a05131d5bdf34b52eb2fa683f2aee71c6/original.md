```
A = JopDct(T, n...[;dims=()])
```

where `A` is a type II discrete cosine transfrom (DCT), T is the element type of the domain and range if A, and n is the size of A.  If `dims` is not set, then `A` is the N-dimensional DCT and where `N=length(n)`.  Otherwise, `A` is a DCT over the dimensions specified by `dims`.

# Examples

## 1D

```julia
A = JopDct(Float64, 128)
m = rand(domain(A))
d = A*m
```

## 2D

```julia
A = JopDct(Float64, 128, 64)
m = rand(domain(A))
d = A*m
```

## 2D transform over 3D array

```julia
A = JopDct(Float64,128,64,32;dims=(1,2))
m = rand(domain(A))
d = A*m
```

# Notes

  * the adjoint pair is achieved by application `sqrt(2/N)` and `sqrt(2)` factors.  See:

      * https://en.wikipedia.org/wiki/Discrete*cosine*transform
      * http://www.fftw.org/fftw3*doc/1d-Real*002deven-DFTs-*0028DCTs*0029.html#g*t1d-Real*002deven-DFTs-*0028DCTs*0029
