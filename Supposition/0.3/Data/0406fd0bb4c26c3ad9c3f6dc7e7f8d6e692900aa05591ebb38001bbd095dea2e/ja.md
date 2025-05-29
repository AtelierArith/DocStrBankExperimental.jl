```
produce!(tc::TestCase, pos::Possibility{T}) -> T
```

与えられた `Possibility` から値を生成し、`TestCase` `tc` に必要な選択を記録します。

これはカスタム `Possibility` オブジェクトのために実装する必要があり、与えられた `tc` を内部の要件に直接渡します。

[`Supposition.produce!`](@ref) も参照してください。

!!! tip "例"
    `Possibility` を持っていて、その `Possibility` によって生成されたオブジェクトがどのように見えるかを調べたい場合は、この関数を呼び出さないでください - その代わりに [`example`](@ref) を使用してください。

