```
donch(hl::Matrix{T}; n::Int64=10, inclusive::Bool=true)::Array{Float64}
```

Donchian channel (if inclusive is set to true, will include current bar in calculations.)

*Output*

  * Column 1: Lowest low of last `n` periods
  * Column 2: Average of highest high and lowest low of last `n` periods
  * Column 3: Highest high of last `n` periods
