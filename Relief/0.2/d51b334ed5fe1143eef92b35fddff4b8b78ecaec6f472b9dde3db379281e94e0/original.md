```
reliefmss(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
               k::Integer=10, dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
               f_type::String="continuous")
```

Compute feature weights using ReliefMSS algorithm. The f_type argument specifies whether the features are continuous or discrete  and can either have the value of "continuous" or "discrete".

---

# Reference:

  * Salim Chikhi and Sadek Benhammada. ReliefMSS: A variation on a

feature ranking ReliefF algorithm. IJBIDM, 4:375–390, 2009.
