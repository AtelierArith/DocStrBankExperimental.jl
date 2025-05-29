```
relief(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
            dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); f_type::String="continuous")::Array{Float64,1}
```

Reliefアルゴリズムを使用して特徴の重みを計算します。f_type引数は、特徴が連続的か離散的かを指定し、"continuous"または"discrete"の値を持つことができます。

---

# 参考文献:

  * Kenji Kira and Larry A. Rendell. The feature selection problem: Tra-

ditional methods and a new algorithm. In Proceedings of the Tenth National Conference on Artificial Intelligence, AAAI’92, pages 129–134. AAAI Press, 1992.
