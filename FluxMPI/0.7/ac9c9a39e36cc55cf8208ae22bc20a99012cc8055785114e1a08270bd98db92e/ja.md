```
allreduce_gradients(gs::NamedTuple; on_gpu::Bool=CUDA.functional())
```

勾配を全体的に集約します。これは、複数のパラメータ配列の大きなコンテナに対して効率的な非ブロッキングAPIを使用します。

## 引数

  * `gs`: 勾配の `NamedTuple`

## キーワード引数

  * `on_gpu`: 勾配がGPU上にあるかどうかを指定します。デフォルトは `CUDA.functional()` です。

## 戻り値

  * 全体的に集約された勾配の `NamedTuple`
