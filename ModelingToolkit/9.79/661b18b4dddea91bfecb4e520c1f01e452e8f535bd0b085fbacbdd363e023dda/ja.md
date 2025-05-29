```julia
liouville_transform(
    sys::ModelingToolkit.AbstractODESystem;
    kwargs...
) -> ModelingToolkit.ODESystem

```

Liouville変換されたODEのセットを生成します。これは、元のODEシステムに新しい変数`trJ`が追加されたもので、-tr(Jacobian)に対応します。この変数は、与えられた初期分布密度からの不確実性伝播などの特性に使用されます。

例えば、$u'=p*u$であり、`p`が確率分布$f(p)$に従う場合、与えられた$p$の選択に対する将来の値の確率密度は、初期の`trJ = f(p)`を設定することによって計算され、`trJ`の最終値は$u(t)$の確率となります。

例:

```julia
using ModelingToolkit, OrdinaryDiffEq

@independent_variables t
@parameters α β γ δ
@variables x(t) y(t)
D = Differential(t)
eqs = [D(x) ~ α*x - β*x*y, D(y) ~ -δ*y + γ*x*y]
@named sys = ODESystem(eqs, t)

sys2 = liouville_transform(sys)
sys2 = complete(sys2)
u0 = [x => 1.0, y => 1.0, sys2.trJ => 1.0]
prob = ODEProblem(sys2, u0, tspan, p)
sol = solve(prob, Tsit5())
```

ここで、`sol[3,:]`は時間に対する`trJ`の進化です。

出典:

F-16コントローラ性能の確率的ロバスト性分析: 最適輸送アプローチ

Abhishek Halder, Kooktae Lee, and Raktim Bhattacharya https://abhishekhalder.bitbucket.io/F16ACC2013Final.pdf
