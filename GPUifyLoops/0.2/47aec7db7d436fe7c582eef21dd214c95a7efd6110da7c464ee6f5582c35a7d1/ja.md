```
contextualize(::Dev, f)
```

この関数は、指定されたデバイスタイプ `Dev` に対して関数 `f` をコンテキスト化します。

デバイス `CUDA()` の場合、`contextualize` は数学ライブラリ関数への呼び出しを置き換えます。例えば、`cos`、`sin` はそれぞれ `CUDAnative.cos`、`CUDAnative.sin` に置き換えられます。

置き換えられる関数の完全なリストは (:cos, :cospi, :sin, :sinpi, :tan, :acos, :asin, :atan, :cosh, :sinh, :tanh, :acosh, :asinh, :atanh, :log, :log10, :log1p, :log2, :exp, :exp2, :exp10, :expm1, :ldexp, :abs, :sqrt, :cbrt, :ceil, :floor) です。

# 例

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
