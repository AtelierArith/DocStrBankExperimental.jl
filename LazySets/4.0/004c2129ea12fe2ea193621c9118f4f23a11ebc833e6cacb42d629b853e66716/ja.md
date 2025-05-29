```
same_block_structure(x::AbstractVector{S1}, y::AbstractVector{S2}
                    ) where {S1<:LazySet, S2<:LazySet}
```

2つの集合のベクトルが同じブロック構造を持っているかどうかを確認します。すなわち、ベクトルの$i$-番目のエントリが同じ次元を持っている必要があります。

### 入力

  * `x` – 最初のベクトル
  * `y` – 2番目のベクトル

### 出力

`true` は、ベクトルが同じブロック構造を持っている場合に限ります。
