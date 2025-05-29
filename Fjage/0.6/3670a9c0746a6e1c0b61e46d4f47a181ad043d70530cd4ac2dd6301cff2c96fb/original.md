```
set!(p::ParameterReq, param, value)
```

Request parameter `param` to be set to `value`.

# Examples

```julia-repl
julia> p = ParameterReq(index=1)
ParameterReq[index=1]
julia> set!(p, "modulation", "ofdm")
ParameterReq[index=1 modulation=ofdm]
julia> set!(p, "fec", 1)
ParameterReq[index=1 modulation=ofdm ...]
```
