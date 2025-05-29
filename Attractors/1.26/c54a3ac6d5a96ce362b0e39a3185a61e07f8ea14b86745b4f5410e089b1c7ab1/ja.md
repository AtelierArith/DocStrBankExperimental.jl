```
`extract_features(mapper, ics; N = 1000, show_progress = true)` を使用して、`ics` の各初期条件の特徴のベクトルを返します（[`basins_fractions`](@ref) のように）。`mapper::AttractorsViaFeaturizing` の設定を使用します。キーワード `N` は `ics isa StateSpaceSet` の場合は無視されます。
```
