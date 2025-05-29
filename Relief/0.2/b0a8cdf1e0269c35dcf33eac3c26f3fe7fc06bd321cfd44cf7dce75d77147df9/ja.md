```
surf(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
     dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
     f_type::String="continuous")::Array{Float64,1}
```

SURFアルゴリズムを使用して特徴の重みを計算します。f_type引数は、特徴が連続的か離散的かを指定し、"continuous"または"discrete"の値を持つことができます。

---

# 参考文献:

  * Casey S. Greene, Nadia M. Penrod, Jeff Kiralis, and Jason H. Moore.

空間的に均一なReliefF (SURF)による遺伝子間相互作用の計算効率的フィルタリング。BioData mining, 2(1):5–5, 2009年9月。
