```
DynamicSS(alg = nothing; tspan = Inf)
```

最初の引数としてODEアルゴリズムが必要です。絶対および相対許容誤差は、導関数がゼロに近いことの終了条件を指定します。これは内部的にCallbackライブラリの`TerminateSteadyState`コールバックを使用します。与えられたODEが解かれるシミュレーション時間は`tspan`によって制限できます。`tspan`が数値の場合、それは`(zero(tspan), tspan)`を渡すことと同等です。

使用例:

```julia
using SteadyStateDiffEq, OrdinaryDiffEq
sol = solve(prob, DynamicSS(Tsit5()))

using Sundials
sol = solve(prob, DynamicSS(CVODE_BDF()); dt = 1.0)
```

!!! note
    デフォルトの`alg`である`nothing`は、`DifferentialEquations.jl`がインストールされ、ロードされている場合にのみ機能します。


!!! note
    `CVODE_BDF`を使用する場合、`dt = ....`を介して開始`dt`を指定する必要があるかもしれません。*

