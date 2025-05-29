```
struct HomogeneousTPTProblem
```

A [`TPTProblem`](@ref) で、遷移行列が均質である、すなわち時間に依存しないものです。

### フィールド

  * `transition_matrix`: A [`TransitionMatrix`](@ref).
  * `source`: TPTソースを定義するインデックスのベクター、すなわち `A`。
  * `target`: TPTターゲットを定義するインデックスのベクター、すなわち `B`。

### コンストラクタ

```
HomogeneousTPTProblem(P, source, target; avoid = Int64[])
```

各引数が対応するフィールドにマッピングされる `HomogeneousTPTProblem` を構築します。

オプション引数 

  * `avoid`: ここに提供されたインデックスは `A` と `B` の両方に追加され、遷移経路理論によって回避されます。
