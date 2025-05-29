```
SimpleBroyden(; linesearch = Val(false), alpha = nothing)
```

Broydenの低オーバーヘッド実装です。このメソッドは、スカラーおよび静的配列の問題に対してメモリを割り当てません。

### キーワード引数

  * `linesearch`: `linesearch`が`Val(true)`の場合、`LiFukushimaLineSearch`ラインサーチを使用します。それ以外の場合はラインサーチは使用されません。ラインサーチの高度なカスタマイズには、`NonlinearSolve.jl`の`Broyden`を使用してください。
  * `alpha`: 初期ヤコビ行列の初期化を`alpha`でスケーリングします。`nothing`の場合、`2 * norm(fu) / max(norm(u), true)`を使用してスケーリングを計算します。
