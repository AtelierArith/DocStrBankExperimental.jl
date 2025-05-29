```
get_samples(cs::AbstractVector{ConvertedSamples}; skipmissing=true)
```

[`edf_to_onda_samples`](@ref) からの [`ConvertedSamples`](@ref) 出力のコレクションから `Onda.Samples` を抽出します。

`skipmissing=true`（デフォルト） の場合、成功裏に変換されたサンプルのみが返されます。 `skipmissing=false` の場合、一部の要素が `missing` になる可能性があります。
