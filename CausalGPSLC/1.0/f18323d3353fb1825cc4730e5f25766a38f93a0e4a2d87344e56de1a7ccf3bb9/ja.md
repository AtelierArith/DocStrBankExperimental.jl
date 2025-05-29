```
extractParameters(g, posteriorSampleIdx)
```

`g`の`posteriorSampleIdx`*番目*の事後サンプルから推定されたパラメータを取得します。 パラメータは`uyLS, xyLS, tyLS, yNoise, yScale, U`であり、その中のいくつかは`Nothing`であることが許可されています。
