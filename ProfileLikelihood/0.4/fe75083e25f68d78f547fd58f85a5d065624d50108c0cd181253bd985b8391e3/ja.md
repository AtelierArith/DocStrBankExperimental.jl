```
struct GridSearch{F,G}
```

`GridSearch`の構造体。

# フィールド

  * `f::F`: 最適化する関数で、形式は`f(x, p)`です。
  * `p::P`: 関数`f`の引数`p`。
  * `grid::G`: グリッドで、`G<:AbstractGrid`です。詳細は[`grid_search`](@ref)を参照してください。
