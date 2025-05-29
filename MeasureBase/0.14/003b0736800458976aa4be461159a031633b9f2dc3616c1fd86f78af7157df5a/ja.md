`logdensity_def` は新しい測度の対数密度を定義する標準的な方法です。この定義にはサポート内のメンバーシップのチェックは含まれていないことに注意してください。これは代わりに `insupport` を使用してチェックされます。`logdensity_def` は低レベルの関数であり、通常は直接呼び出すべきではありません。詳細や他の代替手段については `logdensityof` を参照してください。

---

```
logdensity_def(m, x)
```

測度 m の点 `x` における対数密度を `basemeasure(m)` に対して計算し、`insupport(m, x)` を仮定します。

---

```
logdensity_def(m1, m2, x)
```

点 `x` における `m1` の対数密度を `m2` に対して計算し、`insupport(m1, x)` および `insupport(m2, x)` を仮定します。
