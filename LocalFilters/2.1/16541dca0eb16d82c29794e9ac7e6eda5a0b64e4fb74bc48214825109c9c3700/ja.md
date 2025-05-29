```
convolve!(dst, A, B) -> dst
```

は、`A` の離散畳み込みをカーネル `B` で行い、`dst` を上書きして `dst` を返します。

他に [`convolve`](@ref) と [`localfilter!`](@ref) も参照してください。
