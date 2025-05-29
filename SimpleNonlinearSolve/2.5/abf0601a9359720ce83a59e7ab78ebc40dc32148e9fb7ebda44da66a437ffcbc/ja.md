```
SimpleLimitedMemoryBroyden(;
    threshold::Union{Val, Int} = Val(27), linesearch = Val(false), alpha = nothing
)
```

Broydenの制限付きメモリ実装です。このメソッドは、BroydenのメソッドにL-BFGSスキームを適用します。

しきい値が問題のサイズより大きい場合、このメソッドは`SimpleBroyden`を使用します。

### キーワード引数:

  * `linesearch`: `linesearch`が`Val(true)`の場合、`LiFukushimaLineSearch`ラインサーチを使用します。それ以外の場合はラインサーチは使用されません。ラインサーチの高度なカスタマイズには、`NonlinearSolve.jl`の`Broyden`を使用してください。
  * `alpha`: 初期ヤコビアンの初期化を`alpha`でスケーリングします。`nothing`の場合、`2 * norm(fu) / max(norm(u), true)`を使用してスケーリングを計算します。

!!! warning
    現在、`alpha`はStaticArray問題にのみ使用されます。これは将来的に修正される予定です。

