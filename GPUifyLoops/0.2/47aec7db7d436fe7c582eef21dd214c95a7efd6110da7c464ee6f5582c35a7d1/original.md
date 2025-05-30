```
contextualize(::Dev, f)
```

This contexualizes the function `f` for a given device type `Dev`.

For the device `CUDA()`, `contextualize` replaces calls to math library functions.  For example, `cos`, `sin`, are replaced with `CUDAnative.cos`, `CUDAnative.sin`, respectively.

The full list functions that are replaced is (:cos, :cospi, :sin, :sinpi, :tan, :acos, :asin, :atan, :cosh, :sinh, :tanh, :acosh, :asinh, :atanh, :log, :log10, :log1p, :log2, :exp, :exp2, :exp10, :expm1, :ldexp, :abs, :sqrt, :cbrt, :ceil, :floor).

# Examples

```julia
function kernel!(::Dev, A, f) where {Dev}
    @setup Dev
    @loop for i in (1:size(A,1); threadIdx().x)
        A[i] = f(A[i])
    end
end

g(x) = sin(x)
kernel!(A::Array) = kernel!(CPU(), A, contextualize(CPU(), g))
kernel!(A::CuArray) =
    @cuda threads=length(A) kernel!(CUDA(), A, contextualize(CUDA(), g))

a = rand(Float32, 1024)
b, c = copy(a), CuArray(a)

kernel!(b)
kernel!(c)

@assert g.(a) ≈ b
@assert g.(a) ≈ c
```
