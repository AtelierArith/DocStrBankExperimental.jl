```julia
sequencing(depths, guides, samples)

```

次世代シーケンシングをシミュレートし、各ビン内の各ガイドの頻度に基づいてカテゴリカル分布を生成し、その後、各ビンに対して`depths`で提供された深さまでこの分布からランダムにサンプリングします。ビン名をキーとするDataFrameの辞書を返します。このオブジェクトは、[`Crispulator.counts_to_freqs`](@ref)を通過させた後、[`Crispulator.differences_between_bins`](@ref)に渡すことができます。
