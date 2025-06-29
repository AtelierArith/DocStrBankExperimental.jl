```julia
sigwait(mask, timeout=Inf) -> signum
```

呼び出しスレッドの実行を、一時的に信号セット `mask` で指定された信号のいずれかが保留状態になるまで停止します。この関数は信号を受け入れ（保留中の信号リストから削除し）、信号番号 `signum` を返します。

オプションの引数 `timeout` を指定することで、信号が保留状態になるまでの待機時間に制限を設けることができます。`timeout` は、秒数を指定する実数または [`TimeSpec`](@ref) のインスタンスにすることができます。`timeout` が `Inf`（デフォルト）の場合、待機時間に制限はないと見なされます。`timeout` がゼロ以下の秒数であるか、`timeout` が `TimeSpec(0,0)` の場合、メソッドはポーリングを行い、すぐに戻ります。指定された信号セット `mask` のいずれの信号も許可された待機時間内に保留状態にならなかった場合、[`TimeoutError`](@ref) 例外がスローされます。

関連情報: [`sigwait!`](@ref), [`TimeSpec`](@ref), [`TimeoutError`](@ref).
