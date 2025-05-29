```
ExactDiagonalizationProblem(hamiltonian::AbstractHamiltonian, [v0]; kwargs...)
```

[`AbstractHamiltonian`](@ref) `hamiltonian`を用いて、厳密対角化問題を定義します。オプションで、[`AbstractDVec`](@ref)型の開始ベクトル、または単一のアドレスまたはアドレスのコレクションを`v0`として渡すことができます。

`ExactDiagonalizationProblem`sは[`solve`](@ref solve(::ExactDiagonalizationProblem))を用いて解決できます。

# キーワード引数

  * `algorithm=LinearAlgebraSolver()`: 問題を解くために使用するアルゴリズム。アルゴリズムは`init`関数の第2位置引数としても指定できます。
  * オプションのキーワード引数は、`init`および`solve`関数に渡されます。

# アルゴリズム

  * [`LinearAlgebraSolver()`](@ref): `LinearAlgebra`標準ライブラリの密行列固有値ソルバーを使用して問題を解くためのアルゴリズム（最終的にはLAPACKを使用）。小さな行列にのみ適しています。
  * [`KrylovKitSolver(matrix_free=true)`](@ref): 数個の固有値とベクトルを見つけるためのアルゴリズム。`matrix_free=true`の場合、行列を生成せずに問題が解決されます。これは大きな次元に適しています。`matrix_free=false`の場合、スパース行列を生成した後に問題が解決されます。十分なメモリがある場合、こちらの方が速いです。`using KrylovKit`が必要です。
  * [`ArpackSolver()`](@ref): スパース行列を生成した後、Arpack Fortranライブラリを使用して問題を解くためのアルゴリズム。`using Arpack`が必要です。
  * [`LOBPCGSolver()`](@ref): LOBPCGメソッドを使用してスパース行列を生成した後に問題を解くためのアルゴリズム。`using IterativeSolvers`が必要です。

# 行列ベースのアルゴリズム用のキーワード引数（[`init`](@ref init(::ExactDiagonalizationProblem))でも受け入れられます）

詳細については[`BasisSetRepresentation`](@ref)を参照してください。

  * `sizelim`: 基底集合表現の最大サイズ。スパース行列の場合のデフォルトは`10^6`、密行列の場合のデフォルトは`10^5`です。
  * `cutoff`: 基底集合表現のカットオフ値。
  * `filter`: 基底集合表現のフィルタ関数。
  * `max_depth = Inf`: 行列を構築する際の深さの制限。
  * `minimum_size = Inf`: このサイズに達した後、行列の構築を停止します。
  * `nnzs = 0`: 基底集合表現における非ゼロ要素の数のヒント。非ゼロ値を設定することで計算を高速化できます。
  * `col_hint = 0`: 基底集合表現における列数のヒント。
  * `sort = false`: 基底集合表現をソートするかどうか。

# 反復アルゴリズム用のキーワード引数（[`solve`](@ref solve(::ExactDiagonalizationProblem))でも受け入れられます）

  * `verbose = false`: 追加情報を印刷するかどうか。
  * `abstol = nothing`: ソルバーの絶対許容誤差。`nothing`の場合、ソルバーはデフォルト値を選択します。
  * `howmany = 1`: 計算する固有値の最小数。
  * `which = :SR`: 最大または最小の固有値を計算するかどうか。
  * `maxiters = nothing`: ソルバーの最大反復回数。`nothing`の場合、ソルバーはデフォルト値を選択します。

# `ExactDiagonalizationProblem`の解決

[`solve`](@ref solve(::ExactDiagonalizationProblem))関数は、`ExactDiagonalizationProblem`に対して直接呼び出して解決できます。あるいは、[`init`](@ref init(::ExactDiagonalizationProblem))関数を使用してソルバーを初期化し、その後[`solve`](@ref solve(::ExactDiagonalizationProblem))で解決できます。[`solve`](@ref solve(::ExactDiagonalizationProblem))関数は、固有値、固有ベクトル、および収束情報を含む結果型を返します。

## 結果型

[`solve`](@ref solve(::ExactDiagonalizationProblem))関数の結果型は、使用されるアルゴリズムによって決まります。以下のフィールドがあります：

  * `values::Vector`: 固有値。
  * `vectors::Vector{<:AbstractDVec}`: 固有ベクトル。
  * `success::Bool`: ソルバーが成功したかどうかを示すブールフラグ。
  * `info`: 収束情報。
  * `algorithm`: 計算に使用されたアルゴリズム。
  * `problem`: 解決された`ExactDiagonalizationProblem`。
  * 使用されたアルゴリズムに応じて追加のフィールドが存在する場合があります。

結果型を反復すると、固有値、固有ベクトル、およびその順序でブールフラグ`success`が得られます。

# 例

```jldoctest
julia> p = ExactDiagonalizationProblem(HubbardReal1D(BoseFS(1,1,1)))
ExactDiagonalizationProblem(
  HubbardReal1D(fs"|1 1 1⟩"; u=1.0, t=1.0),
  nothing;
  NamedTuple()...
)

julia> result = solve(p) # 密行列に変換してLinearAlgebra.eigenで解決
EDResult for algorithm LinearAlgebraSolver() with 10 eigenvalue(s),
  values = [-5.09593, -1.51882, -1.51882, 1.55611, 1.6093, 1.6093, 4.0, 4.53982, 4.90952, 4.90952],
  and vectors of length 10.
  Convergence info: "Dense matrix eigensolver solution from `LinearAlgebra.eigen`", with howmany = 10 eigenvalues requested.
  success = true.

julia> using KrylovKit # 外部パッケージをインストールしてロードする必要があります

julia> s = init(p; algorithm = KrylovKitSolver(true)) # 行列を構築せずに解決
KrylovKitDirectEDSolver
 with algorithm KrylovKitSolver(matrix_free = true,) for hamiltonian = HubbardReal1D(fs"|1 1 1⟩"; u=1.0, t=1.0),
  v0 = 1-element PDVec: style = IsDeterministic{Float64}()
  fs"|1 1 1⟩" => 1.0,
  kwargs = NamedTuple()
)

julia> values, vectors, success = solve(s);

julia> result.values[1] ≈ values[1]
true
```

他にも[`solve(::ExactDiagonalizationProblem)`](@ref)、[`init(::ExactDiagonalizationProblem)`](@ref)、[`KrylovKitSolver`](@ref)、[`ArpackSolver`](@ref)、[`LinearAlgebraSolver`](@ref)を参照してください。

!!! note
    `KrylovKitSolver()`アルゴリズムを使用するには、KrylovKit.jlパッケージが必要です。このパッケージは`using KrylovKit`でロードできます。`ArpackSolver()`アルゴリズムを使用するには、Arpack.jlパッケージが必要です。このパッケージは`using Arpack`でロードできます。`LOBPCGSolver()`アルゴリズムを使用するには、IterativeSolvers.jlパッケージが必要です。このパッケージは`using IterativeSolvers`でロードできます。

