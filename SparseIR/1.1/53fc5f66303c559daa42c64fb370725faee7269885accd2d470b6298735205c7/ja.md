```
AugmentedBasis <: AbstractBasis
```

虚時間/周波数軸上の拡張基底。

与えられた `basis` と一緒に追加の関数のセット `augmentations` をグループ化します。拡張された関数は最初の基底関数を形成し、残りは通常の基底によって提供されます。すなわち：

```
u[l](x) == l < naug ? augmentations[l](x) : basis.u[l-naug](x),
```

ここで `naug = length(augmentations)` は拡張によって追加された基底関数の数です。マツバラ周波数についても同様の表現が成り立ちます。

拡張は、自己エネルギーのような頂点状の量の基底を構築する際や、多点関数の基底として機能する二点カーネルを構築する際に有用です [^wallerberger2021] [^shinaoka2018]。

!!! warning
    `TauConst` および `TauLinear` で拡張された基底は、条件が悪くなる傾向があります。フィッティングの際には注意が必要で、問題を正則化するために可能であればコンパクトさを強制するべきです。

    頂点基底、すなわち `MatsubaraConst` で拡張された基底は、比較的条件が良好ですが、可能であればハートリー–フォック項を基底に含めるのではなく、別々に扱うことが良い実践です。


参照：頂点基底のための [`MatsubaraConst`](@ref) [^wallerberger2021]、多点のための [`TauConst`](@ref)、[`TauLinear`](@ref) [^shinaoka2018]

[^wallerberger2021]: https://doi.org/10.1103/PhysRevResearch.3.033168

[^shinaoka2018]: https://doi.org/10.1103/PhysRevB.97.205111
