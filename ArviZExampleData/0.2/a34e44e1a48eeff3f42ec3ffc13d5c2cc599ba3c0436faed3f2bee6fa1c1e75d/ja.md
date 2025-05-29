```
describe_example_data(name) -> String
```

すべての利用可能なデータセットの説明を含む文字列を返します。

# 例

```jldoctest
julia> describe_example_data("radon") |> println
radon
=====

ラドンは、地面との接触点を通じて家に入る放射性ガスです。これは発癌物質であり、非喫煙者の肺癌の主な原因です。ラドンのレベルは家庭ごとに大きく異なります。

この例では、ミネソタ州の家におけるラドンレベルのEPA研究を使用して、郡内の家庭に対する階層を持つモデルを構築します。このモデルには、家庭ごとのウランの文脈効果に対する推定値（ガンマ）が含まれています。

この例の詳細については、Gelman and Hill (2006)を参照するか、Chris Fonnesbeckによるこの実装の詳細についてはhttps://docs.pymc.io/notebooks/multilevel_modeling.htmlを参照してください。

remote: http://ndownloader.figshare.com/files/24067472
```
