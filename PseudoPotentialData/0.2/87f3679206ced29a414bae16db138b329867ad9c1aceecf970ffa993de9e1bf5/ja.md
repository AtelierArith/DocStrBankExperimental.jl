```julia
pseudofile(
    family::PseudoPotentialData.PseudoFamily,
    element::Symbol
) -> String

```

特定の `element`（原子記号で識別される）および特定の擬ポテンシャル `family` に対する擬ポテンシャル情報を含むファイルへのフルパスを取得します。
