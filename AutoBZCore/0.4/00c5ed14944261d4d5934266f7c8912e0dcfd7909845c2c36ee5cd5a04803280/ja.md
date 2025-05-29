```
AutoPTR(; norm=norm, a=1.0, nmin=50, nmax=1000, n₀=6, Δn=log(10), keepmost=2, nthreads=1)
```

自動収束を持つ周期的台形法で、`norm`に関してソルバーに渡された許容誤差に従います。これは、[AutoSymPTR.jl](https://github.com/lxvm/AutoSymPTR.jl)の`autosymptr`ルーチンを使用しています。**このアルゴリズムは滑らかな被積分関数に対して最も効率的です**。
