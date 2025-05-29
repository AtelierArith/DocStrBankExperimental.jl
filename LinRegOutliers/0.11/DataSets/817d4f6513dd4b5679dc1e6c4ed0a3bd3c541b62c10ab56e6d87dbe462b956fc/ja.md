```
ソフトドリンク配達データ
```

# コンポーネント

  * `cases::AbstractVector{Float64}`: 独立変数。
  * `distance::AbstractVector{Float64}`: 独立変数。
  * `time::AbstractVector{Float64}`: 従属変数。

# モデル

time ~ distance + cases 

# 参考文献

D. C. Montgomery and E. A. Peck (1992) Introduction to Regression Analysis. Wiley, New York. 
