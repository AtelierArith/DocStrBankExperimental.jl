```
turf(data::Array{<:Real,2}, target::Array{<:Integer,1}, num_it::Integer=50; 
          rba::Any=relieff)::Array{Float64,1}
```

TuRFアルゴリズムを使用して特徴の重みを計算します。rba引数は、データとターゲット値のみを受け入れる（部分適用された）ラップされたRBAアルゴリズムを指定します。

---

# 参考文献:

  * Jason H. Moore と Bill C. White. ゲノム全体の遺伝分析のためのReliefFの調整. Elena Marchiori, Jason H. Moore, および Jagath C. Rajapakse 編集, Evolutionary Computation, Machine Learning and Data Mining in Bioinformatics, ページ 166–175. Springer, 2007.
