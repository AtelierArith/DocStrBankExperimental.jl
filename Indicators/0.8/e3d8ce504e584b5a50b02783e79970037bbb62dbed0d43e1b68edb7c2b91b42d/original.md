```
heikinashi(ohlc::AbstractMatrix{<:Real})::Matrix{Float64}
```

Heikin Ashi

*Output*

  * Column 1: Heikin Ashi open – previous (o+c)/2
  * Column 2: Heikin Ashi high – max(o,h)
  * Column 3: Heikin Ashi low – min(o,l)
  * Column 4: Heikin Ashi close – (o+h+l+c)/4
