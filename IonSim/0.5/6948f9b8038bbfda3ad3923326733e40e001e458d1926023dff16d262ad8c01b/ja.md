```
visualize(lc::LinearChain, axis::String, modes::Vector{<:Int}, format="bars")
```

`lc`の通常モード構造をPlots.jlプロットとして視覚化します。`axis`は"x"、"y"、"z"のいずれか、またはNamedTuple{(:x,:y,:z)}のいずれかである必要があります。`modes`は、プロットに含めるモードを選択するインデックスのベクトルです。スライスもサポートされています。`format`は、"bars"または"circles"のいずれかにすることができます。

インデックスは、選択されたモードのサブセット`selectedmodes(lc)`ではなく、完全な通常モードの説明を指すことに注意してください。
