```
identity_element(G::AbstractLieGroup)
identity_element(G::AbstractLieGroup, T)
identity_element!(G::AbstractLieGroup, e::T)
```

[`Identity`](@ref) の点の表現を [`AbstractLieGroup`](@ref) `G` に対して返します。デフォルトでは、この表現はデフォルトの配列または数値の表現です。複数の表現が存在する場合、型 `T` を使用してそれらを区別でき、[`AbstractLieGroupPoint`](@ref) と [`AbstractLieAlgebraTangentVector`](@ref) の両方に対して提供する必要があります。なぜなら、これらの型のうちの1つだけが2番目のシグネチャに対して利用可能な場合があるからです。

これは、`G` 上の点としての $e$ の対応するデフォルト表現を返します。これは `e` のインプレースで実行できます。
