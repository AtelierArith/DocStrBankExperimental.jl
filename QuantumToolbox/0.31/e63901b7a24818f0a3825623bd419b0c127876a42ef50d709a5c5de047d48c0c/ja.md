```
ghz_state(n::Union{Int,Val}; d::Int=2)
```

一般化された `n`-qudit [グリーンバーガー–ホーン–ツァイリンガー (GHZ) 状態](https://en.wikipedia.org/wiki/Greenberger%E2%80%93Horne%E2%80%93Zeilinger_state) を返します：

$$
\frac{1}{\sqrt{d}} \sum_{i=0}^{d-1} | i \rangle \otimes \cdots \otimes | i \rangle
$$

ここで、`d` は各 qudit の次元を指定します。デフォルトは `d=2`（キュービット）です。

!!! warning "型の安定性に注意！"
    型の安定性を保ちたい場合は、`ghz_state(n)` の代わりに `ghz_state(Val(n))` を使用することをお勧めします。詳細については、[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) と [関連セクション](@ref doc:Type-Stability) を参照してください。

