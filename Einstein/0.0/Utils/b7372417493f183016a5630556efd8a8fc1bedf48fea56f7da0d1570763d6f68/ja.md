```
sum_kahan(v::AbstractVector{T}) where {T<:Number}
```

数値誤差を減らすためのカハン和算法のノイマイアの変種です。

# 注意

  * 大きなベクトルに対しては `sum_xsum` より遅いですが、小さなベクトルに対しては速いです。
  * カハン和の数値安定性を維持しながら、パフォーマンスを向上させるためにループ展開を使用します。可能な場合は、各イテレーションで2つの要素を処理します。

# 参考文献

  * [JuliaMath/KahanSummation.jl](https://github.com/JuliaMath/KahanSummation.jl)
