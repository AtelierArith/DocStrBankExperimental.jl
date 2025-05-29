```
set_solver( 
    field::AbstractField;
    # キーワード引数とデフォルト
    solver::S, 
    preconditioner::PT, 
    convergence, 
    relax,
    smoother=nothing,
    limit=(),
    itmax::Integer=1000, 
    atol=(eps(_get_float(field.mesh)))^0.9,
    rtol=_get_float(field.mesh)(1e-1)
    ) where {S,PT<:PreconditionerType} = begin

    # NamedTupleを返す
    TF = _get_float(field.mesh)
    (
        solver=solver, 
        preconditioner=preconditioner, 
        convergence=convergence |> TF, 
        relax=relax |> TF, 
        smoother=smoother,
        limit=limit,
        itmax=itmax, 
        atol=atol |> TF, 
        rtol=rtol |> TF
    )
end
```

この関数は、XCALibre.jl内で使用されるソルバー設定を提供するために使用されます。内部でフローソルバーによって使用されるソルバー設定を持つ`NamedTuple`を返します。

# 入力引数

  * `field` ソルバー設定が適用されるフィールドへの参照（必要な整数および浮動小数点型を提供するために使用）
  * `solver` Krylov.jlからのソルバーオブジェクトで、`BicgstabSolver`、`CgSolver`、`GmresSolver`のいずれかであり、XCALibre.jlで再エクスポートされています
  * `preconditioner` 使用される前処理器のインスタンス（例：Jacobi()）
  * `convergence` このフィールドの停止基準を設定
  * `relax` 使用される緩和係数を指定（例：緩和なしの場合は1に設定）
  * `smoother` 離散化の前に適用される平滑化方法を指定。現在のところ`JacobiSmoother`のみが選択肢（デフォルトは`nothing`）
  * `limit` 一部のソルバーで解をこの制限内に制約するために使用（例：（最小、最大））。デフォルトは`()`
  * `itmax` 単一のソルバーパスでの最大反復回数（デフォルトは1000）
  * `atol` ソルバーの絶対許容誤差（デフォルトはeps(FloatType)^0.9）
  * `rtol` ソルバーの相対許容誤差を設定（デフォルトは1e-1）
