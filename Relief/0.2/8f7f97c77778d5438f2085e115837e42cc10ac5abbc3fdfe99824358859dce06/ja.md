```
multisurfstar(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
              dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
              f_type::String="continuous")::Array{Float64,1}
```

MultiSURF*アルゴリズムを使用して特徴の重みを計算します。f_type引数は、特徴が連続的か離散的かを指定し、"continuous"または"discrete"の値を持つことができます。

---

# 参考文献:

  * Delaney Granizo-Mackenzie and Jason H. Moore. 複雑な人間の病気の遺伝的分析のための複数の閾値

空間的に均一なReliefF。In Leonardo Vanneschi, William S. Bush, and Mario Giacobini, editors, Evolutionary Computation, Machine Learning and Data Mining in Bioinformatics, pages 1–10. Springer, 2013.
