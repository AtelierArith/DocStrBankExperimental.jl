```
splitter(u::Symbol, n::Int, timeevol = Continuous())
```

入力信号を `n` 個の信号に分割する名前付きシステムを返します。これは、ブロックダイアグラムに入る外部信号を複数の入力に接続する必要がある場合に便利です。使用例については、チュートリアル https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/hinf_connection/ を参照してください。同じ名前の複数の入力ポートに外部入力を接続する別の方法は、`connect(..., unique=false)` を渡すことです。

# 引数:

  * `u`: 分割する信号の名前
  * `n`: 分割数
