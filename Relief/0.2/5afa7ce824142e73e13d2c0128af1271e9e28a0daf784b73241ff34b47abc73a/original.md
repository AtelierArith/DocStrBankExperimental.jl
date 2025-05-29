```
iterative_relief(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Integer=-1, min_incl::Integer=3, 
                      max_iter::Integer=100, dist_func::Any=(e1, e2, w) -> sum(abs.(w.*(e1 .- e2)), dims=2);
                      f_type::String="continuous")::Array{Float64,1}
```

Compute feature weights using Iterative Relief algorithm.

---

# Reference:

  * Bruce Draper, Carol Kaito, and Jose Bins. Iterative Relief. Proceedings

CVPR, IEEE Computer Society Conference on Computer Vision and Pattern Recognition., 6:62 – 62, 2003.
