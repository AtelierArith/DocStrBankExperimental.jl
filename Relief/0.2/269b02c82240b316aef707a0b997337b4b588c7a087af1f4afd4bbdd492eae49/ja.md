```
swrfstar(data::Array{<:Real,2}, target::Array{<:Integer, 1}, m::Signed=-1, 
              dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
              f_type::String="continuous")::Array{Float64,1}
```

SWRF*アルゴリズムを使用して特徴の重みを計算します。f_type引数は、特徴が連続的か離散的かを指定し、"continuous"または"discrete"の値を持つことができます。

---

# 参考文献:

  * Matthew E. Stokes と Shyam Visweswaran.

空間的に重み付けされたReliefアルゴリズムの適用による病気の遺伝的予測因子のランキング。BioData mining, 5(1):20–20, 2012年12月。23198930[pmid].
