```
butcher_product!(t, t1, t2)
```

根付き木の非結合ブッチャー積 `t = t1 ∘ t2` をインプレースで計算します。これは、`t1` の根から `t2` の根へのエッジを追加することで形成されます。

参照: [`∘`](@ref) (利用可能: `\circ` と TAB)。

参考文献: セクション 301

  * Butcher, John Charles. Numerical methods for ordinary differential equations. John Wiley & Sons, 2016.
