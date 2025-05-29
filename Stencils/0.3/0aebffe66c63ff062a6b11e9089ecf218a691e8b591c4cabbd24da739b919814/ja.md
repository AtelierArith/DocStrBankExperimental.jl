```
stencil(A::AbstractStencilArray)
stencil(A::AbstractStencilArray, I...)
```

インデックス `I` に対して隣接する要素が更新された [`Stencil`](@ref) を取得します。

`I` は `CartesianIndex`、`Tuple`、またはスプラット引数であることができます。

`I` を渡さない場合、ステンシルは更新されず、`nothing` 値を含む可能性がありますが、他のメソッドには依然として役立つかもしれません。
