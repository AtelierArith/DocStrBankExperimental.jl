```
islinear(s::AbstractSystem)
```

システム `s` のダイナミクスが線形方程式によって指定されているかどうかを判断します。

### 注意事項

[セクション 2.7, 1] からの概念を採用します。例えば、入力が $x' = f(t, x, u) = A x + B u$ であるシステムは線形です。なぜなら、関数 $f(t, ⋅, ⋅)$ は各 $t ∈ \mathbb{R}$ に対して $(x, u)$ に関して線形だからです。一方で、$x' = f(t, x, u) = A x + B u + c$ はアフィンですが線形ではありません。なぜなら、$(x, u)$ に関して線形ではないからです。

この関数の結果はシステムのタイプのみに依存し、値には依存せず、`typeof(s)` にも適用できます。したがって、システムタイプが線形でないインスタンスを許可する場合、デフォルトで `false` を返します。例えば、多項式システムは非線形である可能性があるため、`islinear` は `false` を返します。

[1] Sontag, Eduardo D. *Mathematical control theory: deterministic finite dimensional systems.* Vol. 6. Springer Science & Business Media, 2013.
