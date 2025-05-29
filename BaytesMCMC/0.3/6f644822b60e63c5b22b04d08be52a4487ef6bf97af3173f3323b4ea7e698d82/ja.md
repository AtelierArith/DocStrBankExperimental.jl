```julia
combine_proposals(
    _rng,
    trajectory,
    z₁,
    z₂,
    logprob2,
    is_forward
)

```

2つの提案 `ζ₁, ζ₂` を `trajectory` 上で結合し、`ζ₂` を選択するための対数確率 `logprob2` を使用します。 `ζ₁` は `is_forward` の場合に限り `ζ₂` の前にあります。

# 例

```julia

```
