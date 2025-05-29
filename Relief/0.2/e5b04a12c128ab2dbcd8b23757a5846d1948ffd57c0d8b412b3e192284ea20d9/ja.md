```
function reliefseq(data::Array{<:Real, 2}, target::Array{<:Integer, 1}, m::Signed=-1, 
                   k_min::Integer=5, k_max::Integer=10, dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
                   mode::String="discrete", sig::AbstractFloat=1.0, f_type::String="continuous")::Array{Float64,1}
```

ReliefSeqアルゴリズムを使用して特徴量の重みを計算します。mode引数は、どのタイプの重み更新を行うかを指定し、「k*nearest」、「diff」または「exp*rank」のいずれかの値を持つことができます（参考文献を参照）。f*type引数は、特徴量が連続的か離散的かを指定し、「continuous」または「discrete」のいずれかの値を持つことができます。sig引数は、modeが「exp*rank」の値を持つときに使用されます。

---

# 参考文献:

  * Brett A. McKinney, Bill C. White, Diane E. Grill, Peter W. Li, Ri-

chard B. Kennedy, Gregory A. Poland, and Ann L. Oberg. ReliefSeq: a gene-wise adaptive-k nearest-neighbor feature selection tool for finding gene-gene interactions and main effects in mRNA-Seq gene expression data. PloS ONE, 8(12):e81527–e81527, Dec 2013.
