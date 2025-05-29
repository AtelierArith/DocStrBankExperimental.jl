```
irelief(data::Array{<:Real,2}, target::Array{<:Integer,1}, max_iter::Integer, k_width::Real, conv_condition::Real, 
             initial_w_div::Real; f_type::String="continuous")::Array{<:AbstractFloat}
```

I-Reliefアルゴリズムを使用して特徴の重みを計算します。f_type引数は、特徴が連続的か離散的かを指定し、"continuous"または"discrete"の値を持つことができます。

---

# 参考文献:

  * Yijun Sun and Jian Li. Iterative RELIEF for feature weighting. In ICML

2006 - Proceedings of the 23rd International Conference on Machine Learning, volume 2006, pages 913–920, 2006.
