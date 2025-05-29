```julia
All(
    constraints::ValueConstraints.Interface.AbstractConstraint...
) -> ValueConstraints.BasicConstraints.Always

```

すべての`constraints`が有効であることを要求する複合制約です。

これは、渡された`constraints`の量に対して[`Exactly`](@ref)制約をインスタンス化するための短縮形です。

ラップされたすべての制約は「即時に」評価されます。つまり、`constraints`の1つが失敗しても、他のすべてがまだ評価されます。
