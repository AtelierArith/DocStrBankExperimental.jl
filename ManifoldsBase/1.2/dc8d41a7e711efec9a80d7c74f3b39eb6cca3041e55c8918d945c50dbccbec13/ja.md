```
check_vector_transport(
    M::AbstractManifold,
    vector_transport_method::AbstractVectorTransportMethod,
    p=rand(M),
    X=rand(M; vector_at=p),
    Y=rand(M; vector_at=p);
    #
    exactness_tol::Real = 1e-12,
    io::Union{IO,Nothing} = nothing,
    limits::Tuple = (-8.0, 0.0),
    log_range::AbstractVector = range(limits[1], limits[2]; length=N),
    N::Int = 101,
    name::String = "逆射影",
    plot::Bool = false,
    second_order::Bool = true
    slope_tol::Real = 0.1,
    error::Symbol = :none,
    window = nothing,
)

```

再射影 `vector_transport_to` が正しいかどうかを数値的に確認するために、$q_i = \exp_p (t_i X)$ という点の集合を選択し、$t$ が `log_range` のすべての値を取るようにして、[`parallel_transport_to`](@ref) をベクトル `Y` に適用した `vector_transport_method` と比較します。

これには、[`AbstractManifold`](@ref) `M` に対して [`exp`](@ref)、[`parallel_transport_to`](@ref)、および [`norm`](@ref) 関数が実装されている必要があります。

これは [Boumal:2023; Section 4.8 or Section 6.8](@cite) に類似した方法を実装しています。

エラーが指定された許容範囲を下回り、メソッドが正確である場合、プロットは生成されないことに注意してください。

# キーワード引数

  * `exactness_tol`:     すべてのエラーがこの許容範囲を下回る場合、微分は正確であると見なされます
  * `io`:                結果を出力するための `IO` を提供します
  * `limits`:            `log_range` の範囲を指定します。これは範囲の指数です
  * `log_range`:         微分線をサンプリングするための点の範囲（対数スケール）を指定します
  * `N`:                 `log_range` のデフォルト範囲 $[10^{-8},10^{0}]$ 内で検証する点の数
  * `name`:              プロットに表示する名前
  * `plot`:              結果をプロットするかどうか（`Plots.jl` がロードされている場合）。プロットは対数-対数スケールです。これは返され、保存することもできます。
  * `second_order`:      再射影が2次であるかどうかを確認します。`false` に設定すると、1次がチェックされます。
  * `slope_tol`:         近似の傾き（全体）の許容範囲
  * `error`:             エラーを報告する方法を指定します：`:none`、`:info`、`:warn`、または `:error` が利用可能です
  * `window`:            傾き推定に使用される `log_range` 内のウィンドウサイズを指定します。デフォルトは、すべてのウィンドウサイズ `2:N` を使用することです。
