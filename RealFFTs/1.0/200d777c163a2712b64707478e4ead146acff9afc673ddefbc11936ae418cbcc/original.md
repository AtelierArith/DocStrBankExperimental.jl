```
RCPair{T<:AbstractFloat}(undef, realsize::Dims, dims=1:length(realsize))
```

Create a buffer for performing in-place fourier transforms (and inverse) on real-valued data. A single underlying buffer can be viewed either as real data or as complex data:

```julia
RC = RCpair{Float64}(undef, (10, 10))
real(RC) # 10×10 real array
complex(RC) # 6×10 complex array
```

`dims` can be used to control which dimensions are transformed.

The user is responsible to keep track of the current state of the buffer:

```julia
copy!(RC, rand(10, 10))   # copies real-valued data into the buffer; `real(RC)` is the relevant view
rfft!(RC)                 # computes the FFT of the real-valued data; now `complex(RC)` is the relevant view
irfft!(RC)                # computes the inverse FFT of the complex-valued data; now `real(RC)` is the relevant view
```
