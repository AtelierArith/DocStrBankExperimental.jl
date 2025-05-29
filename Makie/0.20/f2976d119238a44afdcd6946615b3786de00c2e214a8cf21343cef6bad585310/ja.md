```
ReversibleScale
```

カスタムスケール構造体で、前方および逆の任意のスケール関数を取ります。

## フィールド

  * `forward::Function`: 前方変換 (例: `log10`)
  * `inverse::Function`: 逆変換 (例: `exp10` は `log10` のため、逆 ∘ 前方 ≡ 恒等)
  * `limits::Tuple{Float32, Float32}`: デフォルトの制限 (オプション)
  * `interval::IntervalSets.AbstractInterval`: 有効な制限区間 (オプション)
  * `name::Symbol`
