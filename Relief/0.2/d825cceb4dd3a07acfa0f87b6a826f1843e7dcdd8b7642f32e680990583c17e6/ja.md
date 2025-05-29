```
relieff(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
             k::Integer=5, dist_func::Function=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
             mode::String="k_nearest", sig::Real=1.0, f_type::String="continuous")::Array{Float64,1}
```

ReliefFアルゴリズムを使用して特徴量の重みを計算します。mode引数は、どのタイプの重みの更新を行うかを指定し、"k*nearest"、"diff"、または"exp*rank"のいずれかの値を持つことができます（参照論文を参照）。f*type引数は、特徴量が連続的か離散的かを指定し、"continuous"または"discrete"のいずれかの値を持つことができます。sig引数は、modeが"exp*rank"の値を持つときに使用されます。

---

# 参考文献:

  * Marko Robnik-Šikonja and Igor Kononenko. Theoretical and empirical

analysis of ReliefF and RReliefF. Machine Learning, 53(1):23–69, Oct

2003. 
