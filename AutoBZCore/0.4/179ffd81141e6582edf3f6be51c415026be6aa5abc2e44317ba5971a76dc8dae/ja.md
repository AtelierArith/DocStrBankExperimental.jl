```
MonkhorstPack(; npt=50, syms=nothing, nthreads=1)
```

次元ごとに固定数のk点 `npt` を使用した周期的台形法で、[AutoSymPTR.jl](https://github.com/lxvm/AutoSymPTR.jl) の `PTR` ルールを使用します。 `nthreads` は、被積分関数がある場合にのみ、積分を並列化するために使用されるスレッドの数を設定します。この場合、ユーザーは被積分関数の評価を並列化する必要があります。スレッドを使用しない場合は `nthreads=1` に設定します。**呼び出し元は、積分が `npt` に関して収束していることを確認する必要があります**。
