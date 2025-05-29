```
reliefmss(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
               k::Integer=10, dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
               f_type::String="continuous")
```

ReliefMSSアルゴリズムを使用して特徴量の重みを計算します。f_type引数は、特徴量が連続的か離散的かを指定し、"continuous"または"discrete"の値を持つことができます。

---

# 参考文献:

  * Salim Chikhi and Sadek Benhammada. ReliefMSS: A variation on a

feature ranking ReliefF algorithm. IJBIDM, 4:375–390, 2009.
