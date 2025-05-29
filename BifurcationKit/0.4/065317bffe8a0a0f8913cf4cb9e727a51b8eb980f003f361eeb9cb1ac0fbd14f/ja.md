```julia
SaveAtEvent(positions; use_newton)

```

このイベントは、継続中に使用されるパラメータ値が `positions` の値のいずれかと等しいときの検出を実装します。この状態はその後、ブランチに保存されます。

例えば、`continuation(args...; event = SaveAtEvent((1., 2., -3.)))` のように使用できます。

オプション `use_newton` は、検出を最終化するためにニュートンアルゴリズムの使用をトリガーします。
