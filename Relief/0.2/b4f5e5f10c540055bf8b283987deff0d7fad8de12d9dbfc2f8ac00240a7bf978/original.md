```
relief(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
            dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); f_type::String="continuous")::Array{Float64,1}
```

Compute feature weights using Relief algorithm. The f_type argument specifies whether the features are continuous or discrete  and can either have the value of "continuous" or "discrete".

---

# Reference:

  * Kenji Kira and Larry A. Rendell. The feature selection problem: Tra-

ditional methods and a new algorithm. In Proceedings of the Tenth National Conference on Artificial Intelligence, AAAI’92, pages 129–134. AAAI Press, 1992.
