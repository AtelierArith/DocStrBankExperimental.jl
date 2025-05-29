`spot2forw(s::Vector{Float64})`

calculates the forward rate `f` rate from the spot rate `s`:

`(1 + s[n-1])^(n-1) * (1+f[n]) = (1+s[n])^n`
