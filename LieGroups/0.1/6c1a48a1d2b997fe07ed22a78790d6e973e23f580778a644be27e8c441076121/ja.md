```
compose(G::AbstractLieGroup, g, h)
compose!(G::AbstractLieGroup, k, g, h)
```

二つの $g, h ∈ \mathcal G$ に対して群演算 $g ∘ h$ を [`AbstractLieGroup`](@ref) `G` の上で実行します。これは `h` のインプレースでも行うことができます。

!!! info
    この関数は `g` または/および `h` が [`Identity`](@ref)`(G)` である場合も処理します。これは新しい群演算を実装する際に曖昧さを引き起こす可能性があるため、この関数は実際の群演算の計算のために `_compose` と `_compose!` をそれぞれ呼び出します。これは（非[`Identity`](@ref) ですが、数値的表現かもしれません）要素に対する群演算の実際の計算を意図しています。

