```
lie_bracket!(𝔤::LieAlgebra, X, Y)
lie_bracket!(𝔤::LieAlgebra, Z, X, Y)
```

リーブ括弧 $[⋅,⋅]: \mathfrak g×\mathfrak g → \mathfrak g$ を計算します。この括弧は以下を満たします。

1. $$
    [X,X] = 0
    $$

    すべての $X ∈ \mathfrak g$ に対して
2. ジャコビの恒等式 $[X, [Y,Z]] = [[X,Y],Z] = [Y, [X,Z]]$ がすべての $X, Y, Z ∈ \mathfrak g$ に対して成り立ちます。

計算は `Z` のインプレースで行うことができます。
