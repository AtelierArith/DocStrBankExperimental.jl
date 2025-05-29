```
mixed_volume(F::Vector{<:MP.AbstractPolynomialLike}; show_progress=true, algorithm=:regeneration)
mixed_volume(𝑨::Vector{<:Matrix}; show_progress=true, algorithm=:regeneration)
```

与えられた多項式系 `F` またはサポート `𝑨` によって表される混合体積を計算します。`algorithm` には2つの可能な値があります：

  * `:total_degree`: セクション7.1で説明されている全体次数ホモトピーアルゴリズムを使用します
  * `:regeneration`: セクション7.2で説明されている熱帯再生アルゴリズムを使用します
