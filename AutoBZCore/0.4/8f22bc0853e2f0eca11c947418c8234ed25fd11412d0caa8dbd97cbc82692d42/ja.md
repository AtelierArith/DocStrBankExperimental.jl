```
PTR(; npt=50, nthreads=1)
```

次元ごとに固定数のk点 `npt` を使用した周期的台形法で、[AutoSymPTR.jl](https://github.com/lxvm/AutoSymPTR.jl) の `ptr` ルーチンを使用します。**呼び出し元は、積分が `npt` に関して収束していることを確認する必要があります**。
