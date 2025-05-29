```
surfstar(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
         dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
         f_type::String="continuous")::Array{Float64,1}
```

Compute feature weights using SURF* algorithm. The f_type argument specifies whether the features are continuous or discrete  and can either have the value of "continuous" or "discrete".

---

# Reference:

  * Casey S. Greene, Daniel S. Himmelstein, Jeff Kiralis, and Jason H. Mo-

ore. The informative extremes: Using both nearest and farthest indivi- duals can improve Relief algorithms in the domain of human genetics. In Clara Pizzuti, Marylyn D. Ritchie, and Mario Giacobini, editors, Evolutionary Computation, Machine Learning and Data Mining in Bi- oinformatics, pages 182–193. Springer, 2010.
