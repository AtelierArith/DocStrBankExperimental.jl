```
reconstruct(algo::T, u) where {T<:AbstractImageReconstructionAlgorithm}
```

入力 `u` を使用してアルゴリズム `algo` から画像を再構成します。結果が利用可能になるまで、またはエラーが発生するまで、`algo` はロックされます。
