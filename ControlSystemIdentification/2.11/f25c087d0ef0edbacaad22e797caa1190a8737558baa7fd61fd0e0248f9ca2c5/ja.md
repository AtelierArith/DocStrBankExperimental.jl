```
structured_pem(
    d,
    nx;
    focus = :prediction,
    p0,
    x0 = nothing,
    K0 = focus == :prediction ? zeros(nx, d.ny) : zeros(0,0),
    constructor,
    h = 1,
    metric::F = abs2,
    regularizer::RE = (p, P, simresult) -> 0,
    optimizer = BFGS(
        # alphaguess = LineSearches.InitialStatic(alpha = 0.95),
        linesearch = LineSearches.BackTracking(),
    ),
    store_trace = true,
    show_trace = true,
    show_every = 50,
    iterations = 10000,
    allow_f_increases = false,
    time_limit = 100,
    x_tol = 0,
    f_abstol = 1e-16,
    g_tol = 1e-12,
    f_calls_limit = 0,
    g_calls_limit = 0,
)
```

予測誤差法（PEM）を用いた線形グレイボックスモデルの同定。

この関数は、ここではユーザーが推定モデルの構造を制御する点で[`newpem`](@ref)と異なりますが、`newpem`では一般的なブラックボックス構造が使用されます。

ユーザーは、パラメータベクトル`p`からモデルを構築する関数`constructor(p)`を提供します。この関数は状態空間システムを返さなければなりません。`p0`はパラメータの対応する初期推定値です。`K0`はオブザーバゲインの初期推定値（`focus = :prediction`の場合のみ使用）であり、`x0`は初期条件の初期推定値です（提供されない場合は自動的に推定されます）。

その他のオプションについては、[`newpem`](@ref)を参照してください。
