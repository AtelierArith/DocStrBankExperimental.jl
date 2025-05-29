```
AlignedSpan(sample_rate, span, mode::ConstantSamplesRoundingMode)
```

`mode.start`に従って左端点が丸められ、右端点は左端点と`AlignedSpans.n_samples(sample_rate, duration(span))`で与えられるサンプル数によって決定される`AlignedSpan`を作成します。

インターフェース: `span`は、[`AlignedSpans.start_index_from_time`](@ref)および`TimeSpans.duration`のメソッドを提供する任意の型である可能性があります。

## より詳細な情報

これは、`AlignedSpan(sample_rate, span, mode::ConstantSamplesRoundingMode)`が同じ`sample_rate`および同じ期間の複数の`span`に適用される場合、結果として得られる`AlignedSpan`が同じ数のサンプルを持つように設計されています。

この理由から、`n_samples(span)`関数ではなく`TimeSpans.duration(span)`を定義することを求めています。アイデアは、この特定の`span`における*実際の*サンプル数ではなく、期間と開始時間のみを使用したいということです。

対照的に、[`RoundInward`](@ref)は、`span`内で発生するサンプルのみ（時間の瞬間として）を含む`AlignedSpan`を提供し、[`AlignedSpan(sample_rate, span, ::RoundingModeFullyContainedSampleSpans)`](@ref)は、入力スパンに含まれる各サンプルから次のサンプルが発生するまでの完全なスパンで構成される`AlignedSpan`を提供します。

同じ数のサンプルを持つ連続した非重複の`AlignedSpans`のコレクションを作成したい場合は、代わりに[`consecutive_subspans`](@ref)を使用してください。
