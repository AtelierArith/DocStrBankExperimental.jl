```
wrap_system(name, system, args...; kwargs...)
```

通常、この関数は `system` の型に基づいてディスパッチし、コアダイナミカルシステムをラップする代数エージェントを初期化します。これにより、ユーザーからこのパッケージの内部を隠しながら、サードパーティパッケージの構文を使用してコアダイナミクスを直接指定することができます。

例えば、`wrap_system(name, prob::DiffEqBase.DEProblem)` というメソッドを定義することができ、内部的には `DiffEqAgent` のコンストラクタを呼び出します。

# 例

```julia
wrap_system("ode_agent", ODEProblem(f, u0, tspan))
wrap_system("abm_agent", ABM(agent, space; properties))
```
