```julia
veryform(
    grid::ExtendableGrids.ExtendableGrid,
    v,
    _::Type{<:ExtendableGrids.AbstractGridComponent}
) -> Any

```

デフォルトのveryformメソッド。

"veryform" は "verify and/or transform" を意味し、`setindex!` を介してグリッドに追加されるコンポーネントをチェックし、必要に応じて変換するために呼び出されます。

デフォルトのメソッドはデータをそのまま通過させるだけです。
