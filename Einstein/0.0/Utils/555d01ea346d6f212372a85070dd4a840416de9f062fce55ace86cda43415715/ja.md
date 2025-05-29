```
dot_kahan(v1::StridedVector{T}, v2::StridedVector{T}) where {T<:Number}
```

数値誤差を減らすためのKahan加算アルゴリズムのNeumaierのバリアント。

# 注意

  * 大きなベクトルに対しては`dot_xsum`より遅いが、小さなベクトルに対しては速い。
  * `dot_kahan`と同様のパフォーマンス
  * Kahan加算の数値安定性を維持しながら、パフォーマンスを向上させるためにループの展開を使用。可能な場合は、各イテレーションで2つの要素を処理。

# 参考文献

  * [JuliaMath/KahanSummation.jl](https://github.com/JuliaMath/KahanSummation.jl)
