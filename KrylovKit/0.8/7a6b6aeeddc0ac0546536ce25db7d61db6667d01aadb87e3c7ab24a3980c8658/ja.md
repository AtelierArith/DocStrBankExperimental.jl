```
linsolve(A::AbstractMatrix, b::AbstractVector, [x₀, a₀::Number = 0, a₁::Number = 1]; kwargs...)
linsolve(f, b, [x₀, a₀::Number = 0, a₁::Number = 1]; kwargs...)
# expert version:
linsolve(f, b, x₀, algorithm, [a₀::Number = 0, a₁::Number = 1]; alg_rrule=algorithm)
```

線形システム `(a₀ + a₁ * A)*x = b` または `a₀ * x + a₁ * f(x) = b` の解 `x` を計算します。初期推測 `x₀` を使用することもできます。近似解 `x` と `ConvergenceInfo` 構造体を返します。

### 引数:

線形マップは `AbstractMatrix`（密または疎）または一般的な関数または呼び出し可能オブジェクトであることができます。初期推測が指定されていない場合、`(zero(a₀)*zero(a₁))*b` として選択され、`b` に似たオブジェクトが生成されますが、ゼロで初期化されます。数値 `a₀` と `a₁` はオプションの引数であり、暗黙的に適用されます。つまり、線形マップの適用時間やベクトル `x` と `b` の操作数には寄与しません。

### 戻り値:

戻り値は常に `x, info = linsolve(...)` の形式であり、

  * `x`: 問題の近似解であり、右辺 `b` と似た型ですが、異なる `eltype` を持つ可能性があります
  * `info`: [`ConvergenceInfo`] の型のオブジェクトで、以下のフィールドを持ちます

      * `info.converged::Int`: 解が要求された許容誤差まで収束したかどうかに応じて 0 または 1 の値を取ります
      * `info.residual`: 近似解 `x` の残差 `b - f(x)`
      * `info.normres::Real`: 残差のノルム、すなわち `norm(info.residual)`
      * `info.numops::Int`: 線形マップが適用された回数、すなわち `f` が呼び出された回数、またはベクトルが `A` と掛けられた回数
      * `info.numiter::Int`: Krylov部分空間が再起動された回数（以下を参照）

!!! warning "収束の確認"
    収束した解が見つからなかった場合、警告は表示されないため、常に `info.converged == 1` を確認してください。


### キーワード引数:

キーワード引数は次のように指定されます：

  * `verbosity::Int = 0`: 冗長性レベル、すなわち 0（メッセージなし）、1（最後に単一メッセージ）、2（各反復後の情報）、3（Krylovステップごとの情報）
  * `atol::Real`: 要求された精度、すなわち残差のノルムに対する絶対許容誤差。
  * `rtol::Real`: 右辺 `b` のノルムに対する残差のノルムの相対的な要求精度。
  * `tol::Real`: アルゴリズムによって実際に使用される残差のノルムに対する要求精度；デフォルトは `max(atol, rtol*norm(b))` です。したがって、`atol` と `rtol` を使用するか、直接 `tol` を使用します（この場合、`atol` と `rtol` の値は無視されます）。
  * `krylovdim::Integer`: 構築されるKrylov部分空間の最大次元。
  * `maxiter::Integer`: Krylov部分空間を再構築できる回数；アルゴリズムの詳細については以下を参照してください。
  * `orth::Orthogonalizer`: 使用される直交化方法、[`Orthogonalizer`](@ref) を参照
  * `issymmetric::Bool`: 線形マップが対称である場合、`T<:Real` の場合のみ意味があります
  * `ishermitian::Bool`: 線形マップがエルミートである場合
  * `isposdef::Bool`: 線形マップが正定値である場合

デフォルト値は `atol = KrylovDefaults.tol`、`rtol = KrylovDefaults.tol`、`tol = max(atol, rtol*norm(b))`、`krylovdim = KrylovDefaults.krylovdim`、`maxiter = KrylovDefaults.maxiter`、`orth = KrylovDefaults.orth` で指定されています；詳細については [`KrylovDefaults`](@ref) を参照してください。

最後の3つのパラメータのデフォルト値はメソッドによって異なります。`AbstractMatrix` が使用される場合、`issymmetric`、`ishermitian` および `isposdef` がその行列に対してチェックされます。それ以外の場合、デフォルト値は `issymmetric = false`、`ishermitian = T <: Real && issymmetric` および `isposdef = false` です。

最後のキーワード引数 `alg_rrule` は、`linsolve` が逆モード自動微分が使用される設定で使用される場合にのみ関連します。`linsolve` のためにカスタム `ChainRulesCore.rrule` が定義されており、`alg_rrule` を介して指定できる異なるアルゴリズムを使用して評価できます。`linsolve` のプルバックは、線形マップの（エルミート）随伴を持つ線形システムを解くことを含むため、デフォルト値は同じアルゴリズムを使用することです。このキーワード引数は、このデフォルトの選択が失敗したり、効率的に機能しない場合にのみ使用する必要があります。`alg_rrule` の可能な値とそれが使用されるアルゴリズムへの影響についての詳細は、ドキュメントを確認してください。

### アルゴリズム

最終的な（専門的な）メソッドは、デフォルト値やキーワード引数なしで、最終的に呼び出されるものであり、直接使用することもできます。ここでは、アルゴリズムを明示的に指定します。現在、[`CG`](@ref)、[`GMRES`](@ref) および [`BiCGStab`](@ref) のみが実装されており、`isposdef == true` の場合は `CG` が選択され、それ以外の場合は `GMRES` が選択されます。標準の `GMRES` 用語では、私たちのパラメータ `krylovdim` は *再起動* パラメータと呼ばれ、`maxiter` パラメータは外部反復の回数、すなわち再起動サイクルの数をカウントします。`CG` では、Krylov部分空間は短い再帰関係が使用されるため、暗黙的であり、再起動は必要ありません。したがって、`CG` アルゴリズムによって使用できる最大の `CG` 反復回数として `krylovdim*maxiter` を渡します。
