```julia
ReverseDiffVJP{compile} <: VJPChoice
```

ReverseDiff.jlを使用してベクトル-ヤコビ行列積を計算します。`f`がインプレースの場合、スカラー化された逆モードを実行するために構造体の配列形式を使用し、`f`がアウトオブプレースの場合は配列ベースの逆モードを使用します。

通常、f関数にスカラー化された操作が存在する場合（例えば、Universal Differential Equationsのような科学的機械学習アプリケーション）や、ブールコンパイルが有効になっている場合（すなわち、ReverseDiffVJP(true)）、EnzymeVJPが特定の`f`の選択で失敗した場合に最も高速です。

GPU（CuArrays）をサポートしていません。

## コンストラクタ

```julia
ReverseDiffVJP(compile = false)
```

## キーワード引数

  * `compile`: 逆テープのコンパイルをキャッシュするかどうか。これによりメソッドのパフォーマンスが大幅に向上しますが、ODE/DAE/SDE/DDEの`f`関数に分岐がないことが必要です。
