```
jacobian(fdm, f, x...)
```

`fdm`を使用して`x`における`f`のヤコビアンを近似します。結果は`size(length(y_vec), length(x_vec))`の`Matrix{<:Real}`として返され、`x_vec`は`x`のフラット化されたバージョンであり、`y_vec`は`f(x...)`のフラット化されたバージョンです。フラット化は[`to_vec`](@ref)によって行われます。
