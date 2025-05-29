```
SignalHandlerCallback(affect, signal::Int) <: AbstractCallback
```

指定されたオペレーティングシステムの信号を受信したときに `affect` を実行するコールバックを返します。中断されたときにシミュレーションを優雅に終了するために使用できます。`using InterProcessCommunication.jl` が利用可能である必要があります。おそらく POSIX システムでのみ動作します。詳細は [InterProcessCommunication.jl](https://github.com/emmt/InterProcessCommunication.jl) を参照してください。

## 例

```
cb = InPartS.SignalHandlerCallback(Returns(99), 2)
```

このコールバックは、プロセスが `SIGINT` を受信したとき（つまり、`Ctrl-C` を押したとき、`2` は `SIGINT` を指します）に、リターンコード `99` でシミュレーションを終了します。
