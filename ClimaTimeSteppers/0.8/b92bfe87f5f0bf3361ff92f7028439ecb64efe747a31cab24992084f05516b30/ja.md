```
KrylovMethod(;
    type = Val(Krylov.GmresSolver),
    jacobian_free_jvp = nothing,
    forcing_term = ConstantForcing(0),
    args = (20,),
    kwargs = (;),
    solve_kwargs = (;),
    disable_preconditioner = false,
    verbose = Silent(),
    debugger = nothing,
)
```

ニュートン法のために `Δx[n] ≈ j(x[n]) \ f(x[n])` の近似を見つけます。ここで `‖f(x[n]) - j(x[n]) * Δx[n]‖ ≤ rtol[n] * ‖f(x[n])‖` であり、`rtol[n]` は反復 `n` における強制項の値です。これは `solve_krylov!(::KrylovMethod, cache, Δx, x, f!, f, n, prepare_for_f!, j = nothing)` を呼び出すことによって行われ、ここで `f` は `f(x[n])` であり、指定されている場合、`j` は `j(x[n])` または `j(x[n])` の近似です。Krylov法に渡される `Δx` はインプレースで修正されます。`cache` は `allocate_cache(::KrylovMethod, x_prototype)` を使用して取得でき、`x_prototype` は `x`（および `Δx` と `f`）に類似しています。

これは主に `Krylov.jl` の `Krylov.KrylovSolver` のラッパーです。`allocate_cache` では、ソルバーは `solver = type(l, l, args..., Krylov.ktypeof(x_prototype); kwargs...)` で構築され、ここで `l = length(x_prototype)` であり、`Krylov.ktypeof(x_prototype)` は `x_prototype` を格納するために使用できる `DenseVector` のサブタイプです。デフォルトでは、ソルバーは Krylov.jl のこのソルバーのデフォルトのKrylov部分空間サイズである20のKrylov.GmresSolverです。`solve_krylov!` では、ソルバーは `Krylov.solve!(solver, opj, f; M, ldiv, atol, rtol, verbose, solve_kwargs...)` で実行されます。ソルバーのタイプは `type` に異なる値を指定することによって変更できますが、この値はランタイムコンパイルを避けるために `Val` でラップする必要があります。

`Krylov.solve!` の呼び出しでは、`opj` は `j(x[n])` を表す `LinearOperator` であり、ソルバーは `mul!(jΔx, opj, Δx)` を評価することによって使用します。ジャコビアンフリーJVP（ジャコビアンベクトル積）が指定されている場合、それは `opj` を構築し、`mul!` への呼び出しを評価するために使用されます。そうでない場合、`j` 自体が `opj` を構築するために使用され、`mul!` への呼び出しは `mul!(jΔx, j, Δx)` に簡略化されます。

ジャコビアンフリーJVPと `j` の両方が指定され、`disable_preconditioner` が `false` に設定されている場合、`j` は `j(x[n])` の近似として扱われ、ソルバーを高速化するために（左）前処理行列 `M` として使用されます。そうでない場合、前処理行列は単位行列 `I` に単純に設定されます。キーワード引数 `ldiv` は `true` に設定されているため、ソルバーは `ldiv!(Δx′, M, f′)` を呼び出し、`mul!(Δx′, M, f′)` ではなくなります。ここで `Δx′` と `f′` は、概ね `Δx` と `f` に対応するソルバーの内部変数を示します。言い換えれば、`ldiv` を `true` に設定すると、ソルバーは `M` を `j` の近似として扱い、`j` の近似の逆としてではなくなります。

キーワード引数 `atol` は0に設定されています。なぜなら、他の値に設定されている場合、不等式 `‖f(x[n]) - j(x[n]) * Δx[n]‖ ≤ rtol[n] * ‖f(x[n])‖` は `‖f(x[n]) - j(x[n]) * Δx[n]‖ ≤ rtol[n] * ‖f(x[n])‖ + atol` に変わり、強制項によって提供される収束保証が排除されるからです（ニュートン-クリロフ法が収束するためには、この不等式の右辺が `n` が増加するにつれて0に近づく必要がありますが、`atol` が0でない場合はそれが起こりません）。

ソルバーを構築し実行するために使用されるすべての引数とキーワード引数は、`args`、`kwargs`、および `solve_kwargs` を使用して変更できます。したがって、このラッパーのデフォルトの動作は簡単に上書きでき、明示的にこのラッパーでカバーされていない `Krylov.jl` の機能も引き続き使用できます。

`verbose` が `true` の場合、残差 `‖f(x[n]) - j(x[n]) * Δx[n]‖` はKrylov法の各反復で印刷されます。デバッガが指定されている場合、それは `Kyrlov.solve!` の呼び出しの前に実行されます。
