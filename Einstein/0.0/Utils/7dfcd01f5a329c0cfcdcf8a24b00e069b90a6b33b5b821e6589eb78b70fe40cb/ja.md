```
dot_xsum(x::StridedVector{T}, y::StridedVector{T}) where {T<:Real}
```

2つのベクトルのドット積を拡張精度の累積を使用して計算します。数値精度を向上させるために`xsum`パッケージを使用します。

# 注意

  * 大きなベクトルに対して非常に高速ですが、小さなベクトルに対してはカハン和よりも少し遅くなります。
  * 両方の入力ベクトルは同じ長さでなければならず、パフォーマンスの理由からチェックは行われません。

# 参考文献

  * [neal2015fastexactsummationusing](@citet*)
  * [JuliaMath/Xsum.jl](https://github.com/JuliaMath/Xsum.jl)
  * [Radford Neal / xsum · GitLab](https://gitlab.com/radfordneal/xsum)
