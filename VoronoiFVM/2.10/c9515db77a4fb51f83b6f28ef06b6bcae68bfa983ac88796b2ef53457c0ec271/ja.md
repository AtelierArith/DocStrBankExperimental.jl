```
SolverControl
SolverControl(;kwargs...)
```

時間ステッピング、埋め込み、ニュートン法および線形ソルバー制御のためのソルバー制御パラメータ。すべてのフィールド名は、[`solve(system::VoronoiFVM.AbstractSystem; kwargs...)`](@ref) のキーワード引数として使用できます。

ニュートン法は、初期値 $u_0$ から始めて、反復手順 $u_{i+1}=u_{i} - d_i F'(u_i)^{-1}F(u_i)$ によって $F(u)=0$ を解きます。ここで、$d_i$ は減衰パラメータです。

  * `verbose::Union{Bool, String}`: 冗長性制御。出力カテゴリのコレクションは、以下の文字で構成された文字列で提供されます：

      * a: 割り当て警告
      * d: 非推奨警告
      * e: 時間/パラメータ進化ログ
      * n: ニュートンソルバーログ
      * l: 線形ソルバーログ

    代わりに、Bool 値を指定することもでき、次のようになります。

      * true: "neda"
      * false: "da"

    非推奨警告を含むすべての出力をオフにするには、`verbose=""` を使用します。出力内では、対応するメッセージは '[n]'、`[a]` などでマークされます（'[l]' を除く）。

    出力の印刷とログ出力の切り替えについては、[`log_output!`](@ref) および [`print_output!`](@ref) を参照してください。
  * `abstol::Float64`: 許容誤差（ニュートン更新のノルムに関して）：$\Delta u_i=||u_{i+1}-u_i||_\infty <$ `abstol` の場合に終了します。
  * `reltol::Float64`: 許容誤差（最初の更新のサイズに対して）：$\Delta u_i/\Delta u_1<$ `reltol` の場合に終了します。
  * `maxiters::Int64`: ニュートン反復の最大数。
  * `tol_round::Float64`: 丸め誤差検出の許容誤差：$|\;||u_{i+1}||_1 - ||u_{i}||_1\;|/ ||u_{i}||_1<$ `tol_round` が連続して `max_round` 回発生した場合に終了します。
  * `tol_mono::Float64`: 単調性テストの許容誤差：$\Delta u_i/\Delta u_{i-1}>$ `1/tol_mono` の場合にエラーで終了します。
  * `damp_initial::Float64`: 初期減衰パラメータ $d_0$。収束問題を処理するために、1未満の値に設定します。
  * `damp_growth::Float64`: 減衰パラメータの成長係数：$d_{i+1}=\min(d_i\cdot$ `max_growth` $,1)$。1より大きい必要があります。
  * `max_round::Int64`: 丸め誤差許容範囲内の連続反復の最大数。デフォルトではこの基準は実質的に無効になります。
  * `unorm::Function`: ニュートン更新ノルムの計算
  * `rnorm::Function`: 丸め誤差計算のための関数
  * `method_linear::Union{Nothing, LinearSolve.SciMLLinearSolveAlgorithm}`: 線形システムのためのソルバーメソッド（LinearSolve.jlを参照）。`nothing` が指定された場合、デフォルトでは次のものが選択されます：

      * `UMFPACKFactorization()` は Float64 の疎行列用
      * `SparspakFactorization()` は一般的な数値型の疎行列用。
      * 三重対角行列およびバンド行列用の LinearSolve.jl のデフォルト

    ユーザーは、自分の問題に最適なものを試すべきです。

    可能な代替手段の概要については、[`VoronoiFVM.LinearSolverStrategy`](@ref) を参照してください。
  * `reltol_linear::Float64`:     反復線形ソルバーの相対許容誤差。
  * `abstol_linear::Float64`: 反復線形ソルバーの絶対許容誤差。
  * `maxiters_linear::Int64`: 線形ソルバーの最大反復数
  * `precon_linear::Union{Nothing, Function, ExtendableSparse.AbstractFactorization, LinearSolve.SciMLLinearSolveAlgorithm, Type}`: 線形システムの前処理器のコンストラクタ。これは、AbstractSparseMatrixCSC（例：ExtendableSparseMatrix）を受け取り、`LinearSolve.jl` の意味で前処理器オブジェクトを返す関数 `precon_linear(A)` として機能する必要があります。便利な例：

      * `ExtendableSparse.ILUZero`
      * `ExtendableSparse.Jacobi`

    この機能に簡単にアクセスするには、[`VoronoiFVM.LinearSolverStrategy`](@ref) も参照してください。
  * `keepcurrent_linear::Bool`: 各ニュートンステップで前処理器を更新しますか？これは、LinearSolve のために `reuse_precs=!keepcurrent_linear` に変換されます。
  * `Δp::Float64`: 埋め込みの初期パラメータステップ。
  * `Δp_max::Float64`: 最大パラメータステップサイズ。
  * `Δp_min::Float64`: 最小パラメータステップサイズ。
  * `Δp_grow::Float64`: 最大パラメータステップサイズの成長。
  * `Δp_decrease::Float64`: 拒否時のパラメータステップ減少係数
  * `Δt::Float64`: 初期時間ステップサイズ。
  * `Δt_max::Float64`: 最大時間ステップサイズ。
  * `Δt_min::Float64`: 最小時間ステップサイズ。
  * `Δt_grow::Float64`: 最大時間ステップサイズの成長。
  * `Δt_decrease::Float64`: 拒否時の時間ステップ減少係数
  * `Δu_opt::Float64`: 時間ステッピングと埋め込みのための更新の最適サイズ。アルゴリズムは、「古い」解と「新しい」解のノルムの差をこの値に近づけるようにします。
  * `Δu_max_factor::Float64`: 時間ステッピングと埋め込みのための更新 `Δu` の最大サイズを `Δu_opt` に対して制御します。`Δu > Δu_max_factor*Δu_opt` の時間ステップは拒否されます。
  * `force_first_step::Bool`: 最初の時間ステップを強制します。
  * `num_final_steps::Int64`: ステップサイズの崩壊を防ぐために、時間区間の終わりで調整する最終ステップの数。
  * `handle_exceptions::Bool`: 過渡ソルバーおよびパラメータ埋め込み中の例外を処理します。`true` の場合、ニュートン解法での例外がキャッチされ、埋め込みまたは時間ステップが低下し、解決が再試行されます。さらに、埋め込みまたは時間ステッピングが失敗した場合（例：最小ステップサイズに達したため）、警告が発行され、これまで計算されたすべてのステップを持つ解が返されます。

    そうでない場合（デフォルトでは）エラーがスローされます。
  * `store_all::Bool`: 過渡/埋め込み問題のすべてのステップを保存します：
  * `in_memory::Bool`: 過渡/埋め込み解をメモリに保存します
  * `log::Any`:    履歴を記録します
  * `edge_cutoff::Float64`: 長方形三角形のエッジパラメータカットオフ。
  * `pre::Function`: 時間/埋め込みステップの前に呼び出される関数 `pre(sol,t)`
  * `post::Function`: 成功した時間/埋め込みステップの後に呼び出される関数 `post(sol,oldsol,t,Δt)`
  * `sample::Function`: 各 `t in times[2:end]` に対して呼び出される関数 `sample(sol,t)`
  * `delta::Function`: 時間ステップ誤差推定器。`Δu=delta(system,u,uold,t,Δt)` を計算する関数です。
  * `tol_absolute::Union{Nothing, Float64}`
  * `tol_relative::Union{Nothing, Float64}`
  * `damp::Union{Nothing, Float64}`
  * `damp_grow::Union{Nothing, Float64}`
  * `max_iterations::Union{Nothing, Int64}`
  * `tol_linear::Union{Nothing, Float64}`
  * `max_lureuse::Union{Nothing, Int64}`
  * `mynorm::Union{Nothing, Function}`
  * `myrnorm::Union{Nothing, Function}`

```
