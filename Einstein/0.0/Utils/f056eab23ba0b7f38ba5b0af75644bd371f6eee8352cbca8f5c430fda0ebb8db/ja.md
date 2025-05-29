```
sum_xsum(vec::AbstractVector{Float64})
```

拡張精度蓄積を使用してベクトルの合計を計算します。数値精度を向上させるために `xsum` パッケージを使用します。

# 注意

  * 大きなベクトルに対して非常に高速ですが、小さなベクトル（n ⪅ 80）に対してはカハン和算よりも少し遅くなります。

# 参考文献

  * [neal2015fastexactsummationusing](@citet*)
  * [JuliaMath/Xsum.jl](https://github.com/JuliaMath/Xsum.jl)
  * [Radford Neal / xsum · GitLab](https://gitlab.com/radfordneal/xsum)
