```
orbitsolve(orbit, t, method=Auto())
```

与えられた軌道オブジェクトと時間 `t`（日数単位）に対して、二次体（例：星の周りの惑星）の位置と速度を取得します。

これは `AbstractOrbitSolution` のサブタイプである構造体を出力し、そこから `raoff`、`decoff`、`radvel` などでクエリを実行できます。

これらの量を個別に計算することもできます（ドキュメント文字列を参照）が、複数の量が必要な場合は、軌道解を一度保存するのが最も効率的です。

注意：これらの計算は小角近似を使用しているため、星が観測者から二次体よりもはるかに遠くにある場合にのみ正確です。

関連情報： `orbitsolve_ν`、`orbitsolve_meananom`、`orbitsolve_eccanom`、`projectedseparation`、`raoff`、`decoff`、`radvel`、`propmotionanom`。
