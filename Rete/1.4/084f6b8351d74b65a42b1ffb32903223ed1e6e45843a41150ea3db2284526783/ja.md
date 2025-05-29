```
connect(from::AbstractReteNode, to::AbstractReteNode)
```

は `to` を `from` の出力にし、`from` を `to` の入力にします。

`connect` は [`_add_input`](@ref) と [`_add_output`](@ref) を呼び出してこれを行います。
