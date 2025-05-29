```
ensemble_vote(int_img::IntegralArray, classifiers::AbstractArray) -> Integer
```

与えられた積分画像（`IntegralArray`）を与えられた分類器を使用して分類します。すなわち、すべての分類器の投票の合計が0より大きい場合、画像は肯定的に分類されます（1）；そうでなければ否定的に分類されます（0）。しきい値は0であり、投票は+1または-1になる可能性があります。

つまり、最終的な強い分類器は次のようになります。

$$
h(x) = \begin{cases}
1&\text{if }\sum_{t=1}^{T}\alpha_{th_{t(x)}}\geq\frac{1}{2}\sum_{t=1}^{T}\alpha_t\\
0&\text{otherwise}
\end{cases}
\text{ where }\alpha_t = \log{\left(\frac{1}{\beta_t}\right)}
$$

# 引数

  * `int_img::IntegralArray{T, N}`: 分類される積分画像
  * `classifiers::Vector{HaarLikeObject}`: 分類器のリスト

# 戻り値

  * `vote::Int8`   1       ⟺ 分類器の投票の合計 > 0   0       それ以外
