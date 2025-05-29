```
Δrst, Rrst = subcell_limiting_operators(rd::RefElemData)
```

サブセル制限演算子のタプル Drst = (Δr, Δs, ...) と R = (Rr, Rs, ...) を返します。ここで、r の合計が 0 の場合、任意の θ の選択に対して sum(D * Diagonal(θ) * R * r) = 0 となります。これらの演算子は、保守的なサブセル制限技術に役立ちます（テンソル積要素に対するこのアプローチの例については、https://doi.org/10.1016/j.compfluid.2022.105627 を参照してください）。

これらのサブセル制限演算子を構築する中間ステップで使用されるスパース SBP 演算子。デフォルトでは、これらの演算子は `sparse_low_order_SBP_operators` を使用して構築されます。一般的な SBP 演算子のためのサブセル制限演算子を構築するには、次のようにします：

```
Δ, R = subcell_limiting_operators(Q::AbstractMatrix; tol = 100 * eps())
```
