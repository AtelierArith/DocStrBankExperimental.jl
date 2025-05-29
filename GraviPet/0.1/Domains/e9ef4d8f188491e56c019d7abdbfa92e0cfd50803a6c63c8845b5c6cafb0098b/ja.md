```
abstract type Domain{T}
```

型 `T` の計算ドメイン。関数の*ドメイン*は、その引数の型です。例えば、`Domain{Float64}` は一次元のドメインを表し、`Domain{SVector{3,Float64}}` は三次元のドメインを表します。

この型はコドメイン、つまり関数の結果の型を表すこともできます。`Domain{Float64}` のコドメインはスカラー関数を表し、`Domain{SVector{3,Float64}}` のコドメインはベクトル値関数を表します。

具体的なドメイン型については、[`Interval`](#GraviPet.Intervals.Interval) と [`Box`](#GraviPet.Boxes.Box) を参照してください。
