```
isbounded(P::AbstractPolyhedron; [solver]=default_lp_solver(eltype(P)))
```

ポリヘドロンが有界かどうかを確認します。

### 入力

  * `P`       – ポリヘドロン
  * `solver`  – （オプション、デフォルト: `default_lp_solver(N)`）線形計画を解くために使用されるバックエンド

### 出力

ポリヘドロンが有界であれば `true`

### アルゴリズム

まず、ポリヘドロンが `dim(P)` よりも多くの制約を持っているかどうかを確認します。これは有界性の必要条件です。

そうであれば、`_isbounded_stiemke` を介して有界性を確認します。
