```
Periodic(frequency)
```

与えられた頻度での周期的な利子複利を表す型です。

`frequency` は `Integer` に変換され、8 桁の小数点以下に丸められます（そうでない場合は `InexactError` が発生します）。

# 例

半年ごとの債券等価利回りを作成する：

```julia-repl
julia> Rate(0.01,Periodic(2))
Rate(0.01, Periodic(2))
```

参照： [`Continuous`](@ref)
