```julia
FunctionCallingCallback(func;
    funcat = Vector{Float64}(),
    func_everystep = isempty(funcat),
    func_start = true,
    tdir = 1)
```

関数呼び出しコールバックを使用すると、興味のある時点で呼び出される関数 `func(u,t,integrator)` を定義できます。コンストラクタは次のとおりです：

  * `func(u, t, integrator)` は呼び出される関数です。
  * `funcat` は関数が評価されることが確実な値または区間です。
  * `func_everystep` は各インテグレータステップの後に関数を呼び出すかどうかです。
  * `func_start` は初期条件で関数が呼び出されるかどうかです。
  * `tdir` は `sign(tspan[end]-tspan[1])` である必要があります。デフォルトは `1` で、`tspan[1] > tspan[end]` の場合は適応する必要があります。
