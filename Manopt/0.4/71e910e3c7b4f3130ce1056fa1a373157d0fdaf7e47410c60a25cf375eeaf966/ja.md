```
quasi_Newton!(M, F, gradF, x; options...)
```

マニフォールド `M` 上の点 `x` から始めて、リトラクション $R$ とベクトル輸送 $T$ を使用して、関数 `F` に対して準ニュートン反復を実行します。

# 入力

  * `M`     マニフォールド $\mathcal{M}$。
  * `F`     最小化するコスト関数 $F: \mathcal{M} →ℝ$。
  * `gradF` 関数 `F` の勾配 $\operatorname{grad}F : \mathcal{M} → T_x\mathcal M$、`gradF(M,p)` として実装されています。
  * `x`     初期値 $x ∈ \mathcal{M}$。

すべてのオプションパラメータについては、[`quasi_Newton`](@ref) を参照してください。 ```
