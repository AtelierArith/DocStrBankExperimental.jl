```
struct ErrorLogger <: Logger
ErrorLogger(nof_eigvals=100,nof_iters=100,displaylevel=1)
```

このオブジェクトを使用して、メソッド内でエラーヒストリーを保存したい場合に使用します。`displaylevel`は`PrintLogger`と同様に解釈されます。キーワード引数`nof_eigvals`と`nof_iters`は、保存に使用されるメモリを事前に割り当てるために使用されます。

このロガーを使用すると、`push_iteration_info!`呼び出しのエラーが`logger.errs`に保存されます。
