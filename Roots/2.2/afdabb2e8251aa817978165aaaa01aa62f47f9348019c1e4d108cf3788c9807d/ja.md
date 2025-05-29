```
Order16()
Thukral16()
```

R. Thukralによる*New Sixteenth-Order Derivative-Free Methods for Solving Nonlinear Equations*に基づくオーダー16アルゴリズムを実装します。American Journal of Computational and Applied Mathematics p-ISSN: 2165-8935; e-ISSN: 2165-8943; 2012; 2(3): 112-118 DOI: [10.5923/j.ajcam.20120203.08](https://doi.org/10.5923/j.ajcam.20120203.08)。

ステップごとに5回の関数呼び出しが必要です。急速に収束しますが、この方法は一般的に他の方法よりも速くはありません（関数呼び出し/ステップが少ない）`Float64`値を使用する場合ですが、`BigFloat`での解決には有用かもしれません。`Order16`メソッドは、`f(x)`が大きいときにSteffensenステップをセカントステップに置き換えます。

誤差`eᵢ = xᵢ - α`は、論文の式(50)における明示的な`K`に対して`eᵢ₊₁ = K⋅eᵢ¹⁶`として表現されます。
