```julia
mutable struct SolverControl
```

時間ステッピング、埋め込み、ニュートン法制御のためのソルバー制御パラメータ。すべてのフィールド名は、[`solve(system::VoronoiFVM.AbstractSystem; kwargs...)`](@ref) のキーワード引数として使用できます。

ニュートン法は、$F(u)=0$ を反復手順 $u_{i+1}=u_{i} - d_i F'(u_i)^{-1}F(u_i)$ によって解きます。ここで、初期値 $u_0$ から始まり、$d_i$ は減衰パラメータです。

  * `tol_absolute::Float64`: 許容誤差（ニュートン更新のノルムに関して）：$\Delta u_i=||u_{i+1}-u_i||_\infty <$ `tol_absolute` の場合に終了します。デフォルト: 1.0e-10
  * `tol_relative::Float64`: 最初の更新のサイズに対する許容誤差：$\Delta u_i/\Delta u_1<$ `tol_relative` の場合に終了します。デフォルト: 1.0e-10
  * `tol_round::Float64`: 丸め誤差検出のための許容誤差：$|\;||u_{i+1}||_1 - ||u_{i}||_1\;|/ ||u_{i}||_1<$ `tol_round` が `max_round` 回連続して発生した場合に終了します。デフォルト: 1.0e-10
  * `tol_mono::Float64`: 単調性テストのための許容誤差：$\Delta u_i/\Delta u_{i-1}>$ `1/tol_mono` の場合にエラーで終了します。デフォルト: 0.001
  * `damp_initial::Float64`: 初期減衰パラメータ $d_0$。収束問題を処理するために、1未満の値に設定します。デフォルト: 1.0
  * `damp_growth::Float64`: 減衰パラメータの成長係数：$d_{i+1}=\min(d_i\cdot$ `max_growth` $,1)$。1より大きい必要があります。デフォルト: 1.2
  * `max_iterations::Int64`: 最大反復回数。デフォルト: 100
  * `max_lureuse::Int64`: LU因子分解の再利用の最大回数。この値が0の場合、線形システムはスパース直接ソルバーによって解かれ、すべてのニュートンステップでLU因子分解が呼び出されます。それ以外の場合、線形システムの解法にはBICGstab反復法が使用され、LU因子分解が前処理器として使用され、`max_lureuse` ニュートンステップごとにのみ更新されます。デフォルト: 0
  * `max_round::Int64`: 丸め誤差許容範囲内での連続反復の最大回数。デフォルトではこの基準は実質的に無効になります。デフォルト: 1000
  * `tol_linear::Float64`: 反復線形ソルバーの相対許容誤差。デフォルト: 0.0001
  * `max_iterations_linear::Int64`: デフォルト: 20
  * `factorization::Union{Symbol, ExtendableSparse.AbstractFactorization}`: 線形システムの因子分解の種類（ExtendableSparse.jlを参照）。可能な値：

      * :lu, :default  : UMFPACKからのLU因子分解（Float64用）またはSparspak.jl
      * :sparspak  : SparspakからのLU因子分解
      * :pardiso  : pardiso.orgのPardisoを使用したPardiso.jlからのLU因子分解。これを使用するには、Pardiso.jlをインストールして`use`します。
      * :mklpardiso  : MKL Pardisoを使用したPardiso.jlからのLU因子分解。これを使用するには、Pardiso.jlをインストールして`use`します。
      * :ilu0 : ゼロフィルILU因子分解前処理器
      * :jacobi : ジャコビ（対角）前処理器

    デフォルト: :lu
  * `max_linear_iterations::Int64`: 線形ソルバーの最大反復回数。デフォルト: 100
  * `gmres_restart::Int64`: 再起動のためのGMRESクリロフ次元。デフォルト: 10
  * `iteration::Symbol`: 因子分解が不完全な場合の反復ソルバー。現在サポートされているもの：

      * :bicgstab : IterativeSolvers.jlからのbicgstabl法
      * :cg : IterativeSolvers.jlからのcg法
      * :krylov_cg : Krylov.jlからのcg法
      * :krylov_bicgstab : Krylov.jlからのbicgstab法
      * :krylov_gmres : Krylov.jlからのgmres法

    デフォルト: :bicgstab
  * `verbose::Bool`: 詳細フラグ。デフォルト: false
  * `handle_exceptions::Bool`: 過渡ソルバーおよびパラメータ埋め込み中の例外を処理します。`true` の場合、ニュートン解法での例外がキャッチされ、埋め込みまたは時間ステップが低下し、解決が再試行されます。デフォルト: false
  * `Δp::Float64`: 埋め込みの初期パラメータステップ。デフォルト: 1.0
  * `Δp_max::Float64`: 最大パラメータステップサイズ。デフォルト: 1.0
  * `Δp_min::Float64`: 最小パラメータステップサイズ。デフォルト: 0.001
  * `Δp_grow::Float64`: 最大パラメータステップサイズの成長。デフォルト: 1.0
  * `Δt::Float64`: 初期時間ステップサイズ。デフォルト: 0.1
  * `Δt_max::Float64`: 最大時間ステップサイズ。デフォルト: 1.0
  * `Δt_min::Float64`: 最小時間ステップサイズ。デフォルト: 0.001
  * `Δt_grow::Float64`: 最大時間ステップサイズの成長。デフォルト: 1.2
  * `Δu_opt::Float64`: 時間ステッピングと埋め込みのための更新の最適サイズ。アルゴリズムは、「古い」解と「新しい」解のノルムの差をこの値に近づけるようにします。デフォルト: 0.1
  * `force_first_step::Bool`: 最初の時間ステップを強制します。デフォルト: false
  * `edge_cutoff::Float64`: 長方形三角形のエッジパラメータカットオフ。デフォルト: 0.0
  * `umfpack_pivot_tolerance::Float64`: umfpackのピボット許容誤差。デフォルト: default*umfpack*pivot_tolerance
  * `store_all::Bool`: 過渡/埋め込み問題のすべてのステップを保存します。デフォルト: true
  * `in_memory::Bool`: 過渡/埋め込み解をメモリに保存します。デフォルト: true
  * `log::Any`: 履歴を記録します。デフォルト: false
