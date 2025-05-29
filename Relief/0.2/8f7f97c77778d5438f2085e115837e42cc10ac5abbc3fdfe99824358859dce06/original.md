```
multisurfstar(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
              dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
              f_type::String="continuous")::Array{Float64,1}
```

Compute feature weights using MultiSURF* algorithm. The f_type argument specifies whether the features are continuous or discrete  and can either have the value of "continuous" or "discrete".

---

# Reference:

  * Delaney Granizo-Mackenzie and Jason H. Moore. Multiple threshold

spatially uniform ReliefF for the genetic analysis of complex human diseases. In Leonardo Vanneschi, William S. Bush, and Mario Giacobini, editors, Evolutionary Computation, Machine Learning and Data Mining in Bioinformatics, pages 1–10. Springer, 2013.
