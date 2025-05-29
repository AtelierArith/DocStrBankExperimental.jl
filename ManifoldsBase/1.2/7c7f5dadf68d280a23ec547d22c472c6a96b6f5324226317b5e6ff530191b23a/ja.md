```
check_inverse_retraction(
    M::AbstractManifold,
    inverse_rectraction_method::AbstractInverseRetractionMethod,
    p=rand(M),
    X=rand(M; vector_at=p);
    #
    exactness_tol::Real = 1e-12,
    io::Union{IO,Nothing} = nothing,
    limits::Tuple = (-8.0, 0.0),
    log_range::AbstractVector = range(limits[1], limits[2]; length=N),
    N::Int = 101,
    name::String = "inverse retraction",
    plot::Bool = false,
    second_order::Bool = true
    slope_tol::Real = 0.1,
    error::Symbol = :none,
    window = nothing,
)
```

逆再traction `inverse_retraction_method` が正しいかどうかを数値的に確認します。これには [`exp`](@ref) および [`norm`](@ref) 関数が [`AbstractManifold`](@ref) `M` に対して実装されている必要があります。

これは [Boumal:2023; Section 4.8 or Section 6.8](@cite) に類似した方法を実装しています。

エラーが指定された許容範囲を下回り、メソッドが正確である場合、プロットは生成されないことに注意してください。

# キーワード引数

  * `exactness_tol`:     すべてのエラーがこの許容範囲を下回る場合、逆再tractionは正確であると見なされます
  * `io`:                結果を印刷するための `IO` を提供します
  * `limits`:            `log_range` の範囲を指定します。すなわち、範囲の指数です
  * `log_range`:         接線ベクトル `X` の長さをサンプリングするためのポイントの範囲（対数スケール）を指定します
  * `N`:                 `log_range` のデフォルト範囲 $[10^{-8},10^{0}]$ 内で検証するポイントの数
  * `name`:              プロットに表示する名前
  * `plot`:              結果をプロットするかどうか（[`plot_slope`](@ref) を参照）プロットは対数-対数スケールです。これは返され、保存することもできます。
  * `second_order`:      再tractionが二次であるかどうかを確認します。`false` に設定すると、一時的な順序が確認されます。
  * `slope_tol`:         近似の傾き（グローバル）の許容範囲
  * `error`:             エラーを報告する方法を指定します： `:none`, `:info`, `:warn`, または `:error` が利用可能です
  * `window`:            傾き推定に使用される `log_range` 内のウィンドウサイズを指定します。デフォルトは、すべてのウィンドウサイズ `2:N` を使用することです。
