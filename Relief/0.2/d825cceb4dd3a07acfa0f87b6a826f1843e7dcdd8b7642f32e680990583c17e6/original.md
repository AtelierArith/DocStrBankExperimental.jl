```
relieff(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
             k::Integer=5, dist_func::Function=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
             mode::String="k_nearest", sig::Real=1.0, f_type::String="continuous")::Array{Float64,1}
```

Compute feature weights using ReliefF algorithm. The mode argument specifies which type of weights update to perform and can either have the value of "k*nearest", "diff" or "exp*rank" (see reference paper). The f*type argument specifies whether the features  are continuous or discrete and can either have the value of "continuous" or "discrete". The sig argument is used when mode has the value of "exp*rank".

---

# Reference:

  * Marko Robnik-Šikonja and Igor Kononenko. Theoretical and empirical

analysis of ReliefF and RReliefF. Machine Learning, 53(1):23–69, Oct

2003. 
