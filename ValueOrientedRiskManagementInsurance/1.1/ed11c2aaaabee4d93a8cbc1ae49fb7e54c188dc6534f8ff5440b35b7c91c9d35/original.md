`forw2spot(f::Vector{Float64})`

calculates the spot rate `s` rate from the forward rate `f`:

`(1+f[1])(1+f[2])...(1+f[n]) = (1+s[n])^n`
