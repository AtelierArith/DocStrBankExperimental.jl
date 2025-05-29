```
initialize_component!(cf::ComponentModel; verbose=true, apply_bound_transformation=true, kwargs...)
```

`ComponentModel`を初期化するには、対応する`NonlinearLeastSquaresProblem`を解決します。初期化中、`default`値を持つすべてのもの（[Metadata](@ref)を参照）を「固定」と見なします。他のすべての変数は「自由」と見なされ、解決されます。各変数の初期推定値は、[Metadata](@ref)の`guess`値に依存します。

結果は`ComponentModel`自体に格納されます。自由変数の値はメタデータフィールド`init`に格納されます。

`kwargs`は非線形ソルバーに渡されます。

## 自由変数の境界

自由変数に境界がある場合、NetworkDynamicsは座標変換を適用することでそれらを保持しようとします。この動作は`apply_bound_transformation`を設定することで抑制できます。以下の変換が使用されます：

  * 両方のaとbが正の(a, b)区間は`u^2`/`sqrt(u)`に変換されます
  * 両方のaとbが負の(a, b)区間は`-u^2`/`sqrt(-u)`に変換されます
