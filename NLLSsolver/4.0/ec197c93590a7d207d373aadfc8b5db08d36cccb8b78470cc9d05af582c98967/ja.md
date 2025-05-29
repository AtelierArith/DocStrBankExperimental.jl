```
NLLSsolver.robustkernel(mycost)
```

`mycost`をロバスト化するための`AbstractRobustifier`のサブタイプを返します。

既存のカーネルには[`NoRobust`](@ref)、[`Scaled`](@ref)、[`HuberKernel`](@ref)、および[`GemanMcclureKernel`](@ref)があります。独自のカーネルを書くこともできます。

!!! tip
    コストが純粋な二乗和（すなわちロバスト化されていない）である場合、このメソッドを実装しないでください。


!!! note
    オプションのユーザー専門API関数です。

