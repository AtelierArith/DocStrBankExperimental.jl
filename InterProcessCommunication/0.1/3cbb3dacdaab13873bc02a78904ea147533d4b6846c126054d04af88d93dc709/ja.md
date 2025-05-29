`SigSet`はCの`sigset_t`構造体を表します。これは*不透明*なものと見なされるべきで、その内容は`sigset_t`のサイズに一致する符号なし整数のタプルとして保存されます。

典型的な使用法は次のとおりです：

```julia
sigset = SigSet()
sigset[signum] -> boolean
sigset[signum] = boolean
fill!(sigset, boolean) -> sigset
```

ここで、`signum`は信号番号で、整数で`1`以上`IPC.SIGRTMAX`以下です。リアルタイム信号は、`IPC.SIGRTMIN ≤ signum ≤ IPC.SIGRTMAX`となる`signum`を持ちます。

非公開メソッド：

```julia
IPC.sigfillset!(sigset)          # fill!(signum, true)と同じ
IPC.sigemptyset!(sigset)         # fill!(signum, false)と同じ
IPC.sigaddset!(sigset, signum)   # sigset[signum] = trueと同じ
IPC.sigdelset!(sigset, signum)   # sigset[signum] = falseと同じ
IPC.sigismember(sigset, signum)  # sigset[signum]と同じ
```
