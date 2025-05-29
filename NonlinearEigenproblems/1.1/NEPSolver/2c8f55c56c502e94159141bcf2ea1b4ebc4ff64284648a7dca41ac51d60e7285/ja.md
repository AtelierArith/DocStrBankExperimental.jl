```
augnewton([eltype], nep::NEP; [errmeasure,][tol,][maxit,][λ,][v,][c,][logger,][linsolvercreator,][armijo_factor,][armijo_max])
```

拡張ニュートン法を実行します。この方法は、正確な算術における `newton()` と同等ですが、長さ `n` のベクトルに対する操作のみで機能します。

以下のキーワード引数は、多くのNEPソルバーで共通です：

  * `logger` は [`Logger`](@ref) オブジェクトまたは `Int` です。`Int` の場合、`PrintLogger(logger)` がインスタンス化されます。`logger=0` は何も印刷せず、`logger=1` はより多くを印刷します。
  * `errmeasure` はエラーの測定方法を決定します。これは関数ハンドルまたは `Errmeasure` 型のオブジェクトです。関数ハンドルの場合、`(λ,v)` を入力として受け取り、実数スカラー（エラー）を返す必要があります。詳細については [`Errmeasure`](@ref) および [`ErrmeasureType`](@ref) を参照してください。
  * `tol` は終了を決定するスカラーです。`errmeasure` が `tol` より小さい場合、固有対は収束したとマークされます。
  * スカラー `λ` とベクトル `v` は開始近似です。
  * `maxit` は最大反復回数を決定します。これを超えるとエラー `NoConvergenceException` がスローされます。
  * `linsolvecreator` は線形システムの解決方法を指定します。詳細については [`LinSolver`](@ref) を参照してください。
  * `armijo_factor` はアルミホルールを適用するかどうかを指定し、その値はステップ長のスケーリングファクター（減少ステップごと）を指定します。変数 `armijo_max` はステップ長の最大減少回数を指定します。

# 例

これは `newton` と `augnewton` の同等性を示しています。

```julia-repl
julia> nep=nep_gallery("dep1")
julia> λ1,v1=newton(nep,maxit=20,v=ones(size(nep,1)),λ=0)
julia> λ2,v2=augnewton(nep,maxit=20,v=ones(size(nep,1)),λ=0)
julia> λ1-λ2
0.0 + 0.0im
```

# 参考文献

  * Nichtlineare Behandlung von Eigenwertaufgaben, Z. Angew. Math. Mech. 30 (1950) 281-282.
  * A. Ruhe, Algorithms for the nonlinear eigenvalue problem, SIAM J. Numer. Anal. 10 (1973) 674-689
