```
is_feasible(M::AbstractManifold, cmo::ConstrainedManifoldObjective, p, kwargs...)
```

点 `p` が [`ConstrainedManifoldObjective`](@ref) `cmo` に関して実現可能かどうかを評価します。つまり、`cmo` 内の提供された不等式制約 $g: \mathcal M → ℝ^m$ と等式制約 $h: \mathcal M \to ℝ^m$ に対して、点 $p ∈ \mathcal M$ は次の条件を満たす場合に実現可能です。

$$
g_i(p) ≤ 0, \text{ for all } i=1,…,m\quad\text{ and }\quad h_j(p) = 0, \text{ for all } j=1,…,n.
$$

# キーワード引数

  * `check_point::Bool=true`: ``p∈\mathcal M` が成り立つことを [`is_point`](@extref ManifoldsBase.is_point) を使用して確認するかどうか。
  * `error::Symbol=:none`: 点が実現可能でない場合、このシンボルはエラーを報告する方法を決定します。

      * `:error`: エラーをスローします
      * `:info`: エラーメッセージを @info として表示します
      * `:none`: (デフォルト) 関数は単に true/false を返します
      * `:warn`: エラーメッセージを @warning として表示します。

キーワード `error=` とその他の `kwargs...` は、点が確認される場合に [`is_point`](@extref ManifoldsBase.is_point) に渡されます（`check_point` を参照）。

その他のキーワードは `is_poi` に渡されます。 ```
