```
ka_diamond(N::Int, ArrayT::Type{<:AbstractArray}) -> Tiling{ArrayT{Edge}}
```

[`diamond`](@ref)と同様に、均一にランダムなダイヤモンドタイルを生成しますが、(GPU)並列処理を活用できるように`KernelAbstractions.jl`を使用します。`ArrayT`は`Array`または任意のGPU配列タイプであることができます。

参照 [`Tiling`](@ref)
