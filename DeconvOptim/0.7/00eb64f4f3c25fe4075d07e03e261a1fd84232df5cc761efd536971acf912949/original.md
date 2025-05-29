```
plan_conv(u, v [, dims])
```

Pre-plan an optimized convolution for arrays shaped like `u` and `v` (based on pre-plan FFT) along the given dimensions `dims`. `dims = 1:ndims(u)` per default. The 0 frequency of `u` must be located at the first entry. We return two arguments:  The first one is `v_ft` (obtained by `fft(v)` or `rfft(v)`). The second return is the convolution function `pconv`. `pconv` itself has two arguments. `pconv(u, v_ft=v_ft)` where `u` is the object and `v_ft` the v_ft. This function achieves faster convolution than `conv(u, u)`. Depending whether `u` is real or complex we do `fft`s or `rfft`s

# Warning

The resulting output of the `pconv` function is a reference to an internal, allocated array. If you use the `pconv` function for different tasks,  a new call to `pconv` will change the previous result (since the previous result was only a reference, not a new array). 

# Examples

```jldoctest
julia> u = [1 2 3 4 5]
1×5 Matrix{Int64}:
 1  2  3  4  5
julia> v = [1 0 0 0 0]
1×5 Matrix{Int64}:
 1  0  0  0  0
julia> v_ft, pconv = plan_conv(u, v);
julia> pconv(u, v_ft)
1×5 Matrix{Float64}:
 1.0  2.0  3.0  4.0  5.0
julia> pconv(u)
1×5 Matrix{Float64}:
 1.0  2.0  3.0  4.0  5.0
```
