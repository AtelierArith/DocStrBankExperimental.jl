```
lorentzfactor(v::Number)
```

ローレンツ因子 $\gamma$ を（座標）速度 $v$ に対して計算します。これは次のように定義されます。

$$
\gamma^{-2} = |1 - v^2|
$$

これはエラーを出さず、通常の空間ベクトルを正規化する際に関連するタキオン速度 $v > 1$ に対して正しい結果を返します。
