```
irelief(data::Array{<:Real,2}, target::Array{<:Integer,1}, max_iter::Integer, k_width::Real, conv_condition::Real, 
             initial_w_div::Real; f_type::String="continuous")::Array{<:AbstractFloat}
```

Compute feature weights using I-Relief algorithm. The f_type argument specifies whether the features are continuous or discrete  and can either have the value of "continuous" or "discrete".

---

# Reference:

  * Yijun Sun and Jian Li. Iterative RELIEF for feature weighting. In ICML

2006 - Proceedings of the 23rd International Conference on Machine Learning, volume 2006, pages 913–920, 2006.
