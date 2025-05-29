```
DirectionalTransiogram(direction, data, var; dtol=1e-6u"m", [options])
```

与えられた `direction` に沿って、地理空間データ `data` に格納されたカテゴリ変数 `var` の経験的トランジオグラムを、長さ単位でのバンド許容誤差 `dtol` を用いて計算します。

`options` を基盤となる [`EmpiricalTransiogram`](@ref) に渡します。
