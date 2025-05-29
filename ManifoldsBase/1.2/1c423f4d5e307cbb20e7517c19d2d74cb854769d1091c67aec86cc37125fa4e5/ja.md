```
fill(p, M::AbstractPowerManifold)
```

[`AbstractPowerManifold`](@ref) `M`上に点を作成し、すべてのエントリを点`p`に設定します。

!!! note
    通常、マニフォールドは`ManifoldsBase.jl`のすべての関数で最初の引数ですが、`fill`のシグネチャに従い、パワーマニフォールドがサイズ情報として機能します。

