```
vlsrelief(data::Array{<:Real,2}, target::Array{<:Integer,1}, subset_size::Integer=-1, 
               num_subsets::Integer=100; rba::Any=relieff)::Array{Float64,1}
```

VLSReliefアルゴリズムを使用して特徴量の重みを計算します。num*partitions*to*select引数は、各イテレーションで選択するパーティションの数を指定します。num*subsets引数は、実行するサブセットイテレーションの数を指定します。subset_size引数は、パーティションのサイズを指定します。rba引数は、データとターゲット値のみを受け入れるべき（部分適用された）ラップされたRBAアルゴリズムを指定します。

---

# 参考文献:

  * Margaret Eppstein and Paul Haake. Very large scale ReliefF for genome-

wide association analysis. In 2008 IEEE Symposium on Computational Intelligence in Bioinformatics and Computational Biology, CIBCB ’08,

2008. 
