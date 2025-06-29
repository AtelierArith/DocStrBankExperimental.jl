```
GeneralizedDFSane(; linesearch, sigma_min, sigma_max, sigma_1, name::Symbol = :unknown)
```

DF-SANEアルゴリズムの一般化されたバージョンです。このアルゴリズムは、ヤコビアンフリーのスペクトル法です。

### 引数

  * `linesearch`: 線形探索法を使用したグローバリゼーション。これは現在必須ですが、その制限は将来的に解除される可能性があります。
  * `sigma_min`: 許可される最小スペクトルパラメータ。これは、スペクトルパラメータが小さすぎないことを保証するために使用されます。
  * `sigma_max`: 許可される最大スペクトルパラメータ。これは、スペクトルパラメータが大きすぎないことを保証するために使用されます。
  * `sigma_1`: 初期スペクトルパラメータ。これが提供されない場合、アルゴリズムは`sigma_1 = <u, u> / <u, f(u)>`として初期化します。
