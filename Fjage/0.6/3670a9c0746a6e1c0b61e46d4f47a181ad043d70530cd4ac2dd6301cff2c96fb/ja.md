```
set!(p::ParameterReq, param, value)
```

リクエストパラメータ `param` を `value` に設定します。

# 例

```julia-repl
julia> p = ParameterReq(index=1)
ParameterReq[index=1]
julia> set!(p, "modulation", "ofdm")
ParameterReq[index=1 modulation=ofdm]
julia> set!(p, "fec", 1)
ParameterReq[index=1 modulation=ofdm ...]
```
