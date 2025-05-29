```
output = knitro(nlp; kwargs...)
```

`NLPModel` 問題 `nlp` を KNITRO を使用して解決します。

高度な使用法では、まず `KnitroSolver` を定義してアルゴリズムで使用されるメモリを事前に割り当て、その後 `solve!` を呼び出します：

```
solver = KnitroSolver(nlp)
solve!(solver, nlp; kwargs...)
solve!(solver, nlp, stats; kwargs...)
```

# オプションのキーワード引数

  * `x0`: 初期プライマル推定を指定するためのサイズ `nlp.meta.nvar` のベクトル
  * `y0`: 一般的な制約の初期デュアル推定を指定するためのサイズ `nlp.meta.ncon` のベクトル
  * `z0`: 制約の初期乗数を指定するためのサイズ `nlp.meta.nvar` のベクトル
  * `callback`: KNITRO によって各イテレーションで呼び出されるユーザー定義の `Function`。

コールバックに関する詳細は、https://www.artelys.com/docs/knitro/2*userGuide/callbacks.html および `KNITRO.KN*set*newpt*callback` のドキュメントを参照してください。

その他のすべてのキーワード引数は、オプションとして KNITRO に渡されます。受け入れられるオプションのリストについては、https://www.artelys.com/docs/knitro/3_referenceManual/userOptions.html を参照してください。
