```
diskmargin(P::LTISystem, C::LTISystem, σ, w::AbstractVector, args...; kwargs...)
```

出力、入力、および `P` の入力/出力の同時ディスクマージン。 `input, output, simultaneous_input, simultaneous_output, simultaneous` というフィールドを持つ名前付きタプルを返します。 `input` と `output` はループごとのマージンを表し、`simultaneous_input` はすべての入力に対する同時摂動のマージンであり、`simultaneous` はすべての入力と出力に対する同時摂動のマージンです。

注意: 同時マージンは単一ループマージンよりも保守的であり、単一ループマージンよりもはるかに低くなる可能性があります。実際、いくつかの同時摂動がある場合、システムを不安定にするのは一般的に容易です。2つの信号を含む同時マージンが単一ループマージンの半分のサイズのオーダーであることは珍しくありません。

[`ncfmargin`](@ref) および [`loop_diskmargin`](@ref) も参照してください。
