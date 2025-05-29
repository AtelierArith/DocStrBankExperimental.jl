```
AutoSymPTRJL(; norm=norm, a=1.0, nmin=50, nmax=1000, n₀=6, Δn=log(10), keepmost=2, nthreads=1)
```

自動収束を持つ周期的台形法で、`norm`に関してソルバーに渡された許容誤差に対して、[AutoSymPTR.jl](https://github.com/lxvm/AutoSymPTR.jl)の`autosymptr`ルーチンを使用します。`nthreads`は、被積分関数がある場合にのみ、積分を並列化するために使用されるスレッドの数を設定します。この場合、ユーザーは被積分関数の評価を並列化する必要があります。スレッドを使用しない場合は`nthreads=1`に設定します。**このアルゴリズムは滑らかな被積分関数に対して最も効率的です**。
