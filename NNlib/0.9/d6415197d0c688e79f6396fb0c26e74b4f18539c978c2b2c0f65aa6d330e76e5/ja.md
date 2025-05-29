```
tanh_fast(x)
```

これは`tanh`のより速いがわずかに精度が低いバージョンです。

Juliaの`tanh`関数は2 eps未満の誤差がありますが、これは5 epsの誤差がある可能性があり、1桁未満の減少です。

`x::Float32`の場合、通常は約10倍速く、`x::Float64`の場合は小さな速度向上があります。他の数値型の場合は、単に`tanh`を呼び出します。

[`sigmoid_fast`](@ref)も参照してください。

```julia-repl
julia> tanh(0.5f0)
0.46211717f0

julia> tanh_fast(0.5f0)
0.46211714f0

julia> hard_tanh(0.5f0)
0.5f0
```
