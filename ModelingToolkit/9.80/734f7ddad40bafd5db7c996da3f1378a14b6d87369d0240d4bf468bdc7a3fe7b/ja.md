```julia
SciMLBase.BVProblem{iip}(sys::AbstractODESystem, u0map, tspan,
                         parammap = DiffEqBase.NullParameters();
                         constraints = nothing, guesses = nothing,
                         version = nothing, tgrad = false,
                         jac = true, sparse = true,
                         simplify = false,
                         kwargs...) where {iip}
```

[`ODESystem`](@ref) から境界値問題を作成します。

`u0map` は状態の固定初期値を指定するために使用されます。すべての変数は、`guesses` を使用して初期推測を提供するか、`u0map` を使用して固定初期値を指定する必要があります。

境界値条件は、ConstraintsSystem の形式で ODESystem に供給されます。これらの方程式は、特定の点で状態変数が取るべき値を指定する必要があります（例：`x(0.5) ~ 1`）。全体の解に対して成り立つべきより一般的な制約（例：`x(t)^2 + y(t)^2`）は、`ODESystem` を構築するために使用される方程式の1つとして指定する必要があります。

`constraints` のない ODESystem が指定された場合、それは初期値問題として扱われます。

```julia
    @parameters g t_c = 0.5
    @variables x(..) y(t) λ(t)
    eqs = [D(D(x(t))) ~ λ * x(t)
           D(D(y)) ~ λ * y - g
           x(t)^2 + y^2 ~ 1]
    cstr = [x(0.5) ~ 1]
    @mtkbuild pend = ODESystem(eqs, t; constraints = cstrs)

    tspan = (0.0, 1.5)
    u0map = [x(t) => 0.6, y => 0.8]
    parammap = [g => 1]
    guesses = [λ => 1]

    bvp = SciMLBase.BVProblem{true, SciMLBase.AutoSpecialize}(pend, u0map, tspan, parammap; guesses, check_length = false)
```

`ODESystem` に代数方程式（例：`x(t)^2 + y(t)^2`）がある場合、結果として得られる `BVProblem` は、Ascher のような BVDAE ソルバーを使用して解決する必要があります。
