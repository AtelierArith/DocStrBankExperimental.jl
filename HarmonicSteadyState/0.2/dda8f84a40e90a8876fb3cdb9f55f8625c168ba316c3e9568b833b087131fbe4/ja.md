```julia
filter_result!(
    res::HarmonicSteadyState.Result,
    class::String
)

```

`res`から`class`に属さない解のすべての解枝を削除します。通常、巨大なファイルサイズを防ぐために非物理的な解をフィルタリングするために使用されます。
