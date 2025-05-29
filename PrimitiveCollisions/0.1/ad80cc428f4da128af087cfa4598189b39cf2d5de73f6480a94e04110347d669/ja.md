```julia
function invert(state::State{R}) where {R}
```

`A`に対する`B`の構成を含む`State`を与えると、`B`に対する`A`の構成を含む状態を返します。
