```
addTerminator(M, Bath)
```

与えられたHEOMLS行列に終端子を追加します。

終端子は、`Bath.Nterm`を超えるすべての指数展開項の系-浴ダイナミクスへの寄与を表すリウヴィル項です。

真の相関関数と`Bath.Nterm`-指数項の合計との違いは、おおよそ`2 * δ * dirac(t)`です。ここで、`δ`は近似の不一致を示し、`dirac(t)`はディラックデルタ関数を示します。

# パラメータ

  * `M::AbstractHEOMLSMatrix` : HEOMモデルから与えられた行列
  * `Bath::Union{BosonBath, FermionBath}` : 近似の不一致δを含む浴オブジェクト

# 戻り値

  * `M_new::AbstractHEOMLSMatrix` : 新しいHEOMリウヴィル超演算子行列

```
