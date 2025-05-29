```
log(G::GeneralLinear, p, q)
```

[`GeneralLinear(n)`](@ref)群の対数写像を計算します。

アルゴリズムは二段階で進行します。まず、点 $r = p^{-1} q$ がフロベニウスノルムの下で直積部分群 $\mathrm{O}(n) × S^+$ の最も近い要素に射影されます。この部分群の対数写像は行列対数を使用して正確に計算されます。この初期接ベクトルは、[`NLSolveInverseRetraction`](@extref `ManifoldsBase.NLSolveInverseRetraction`)を使用して洗練されます。

`GeneralLinear(n, ℂ)`の場合、対数写像は実化されたスーパー群 `GeneralLinear(2n)` 上で計算され、得られた接ベクトルはその後複素化されます。

この実装は実験的であることに注意してください。 ```
