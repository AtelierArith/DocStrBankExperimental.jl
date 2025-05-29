```
fill!(P, p, M::AbstractPowerManifold)
```

点 `P` を [`AbstractPowerManifold`](@ref) `M` に埋め、すべてのエントリを `p` に設定します。

!!! note
    通常、マニフォールドは `ManifoldsBase.jl` のすべての関数で最初の引数ですが、ここでは `fill!` のシグネチャに従い、パワーマニフォールドがサイズ情報として機能します。

