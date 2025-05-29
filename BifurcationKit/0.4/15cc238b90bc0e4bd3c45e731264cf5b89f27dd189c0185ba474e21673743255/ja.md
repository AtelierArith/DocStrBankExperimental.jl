```julia
continuation(
    prob,
    alg,
    contparams;
    linear_algo,
    bothside,
    kwargs...
)

```

関数 `F` に関連する継続曲線を計算します。この関数は分岐問題 `prob` に保存されています。一般的な情報は [Continuation methods: introduction](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/IntroContinuation/) で入手できます。

# 引数:

  * `prob::AbstractBifurcationFunction` は `::AbstractBifurcationProblem` で、通常はベクトル場とそのヤコビ行列を保持する [`BifurcationProblem`](@ref) です。詳細については [`BifFunction`](@ref) を参照してください。
  * `alg` 継続アルゴリズム、例えば `Natural(), PALC(), Multiple(),...`。詳細は [algos](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/Predictors/) を参照してください。
  * `contparams::ContinuationPar` 継続のためのパラメータ。詳細は [`ContinuationPar`](@ref) を参照してください。

# オプション引数:

  * `plot = false` 解/ブランチ/スペクトルを計算中にプロットするかどうか
  * `bothside = true` 初期パラメータ値 `p0` の両側でブランチを計算し、それらをマージして返します。
  * `normC = norm` 非線形解法で使用されるノルム
  * `filename` 継続中に計算されたブランチを保存するためのファイル名。このファイル名には識別子 .jld2 が追加されます。これには `using JLD2` が必要です。
  * `callback_newton` ニュートン反復のためのコールバック。詳細は [`newton`](@ref) のドキュメントを参照してください。例えば、前処理器を変更するために使用できます。
  * `finalise_solution = (z, tau, step, contResult; kwargs...) -> true` 各継続ステップの最後に呼び出される関数。継続手順を変更するために使用できます（`false` を返すことで停止）。個人データを保存したり、プロットしたりすることができます。記法は `z = BorderedArray(x, p)` で、`x`（および `p`）は現在の解（およびパラメータ値）、`tau::BorderedArray` は `z` での接線、`step::Int` は現在の継続ステップのインデックス、`contResult` は現在のブランチです。高度な使用法:

      * 継続イテレータの状態 `state::ContState` が `kwargs` に渡されます。これを使用して、分岐点/イベントを特定するための二分法から呼び出されているかどうかをテストできます: 例えば `in_bisection(state)`。これにより、この場合に個人コードを回避できます。

    イテレータを使用することで継続手順をより良く制御できることに注意してください。詳細は [Iterator Interface](@ref) を参照してください。

      * 継続のイテレータ `iter::ContIterable` が `kwargs` に渡されます。
  * `verbosity::Int = 0` 継続プロセス中に印刷される情報の量を制御します。`{0,1,2,3}` のいずれかである必要があります。`contparams.newton_options.verbose = false` の場合、次のようになります（そうでない場合、ニュートン反復が表示されます）。各ケースは前のケースよりも多くの情報を印刷します:

      * ケース 0: 何も印刷しない
      * ケース 1: 継続に関する基本情報を印刷する: 使用された予測子、ステップサイズ、パラメータ値
      * ケース 2: ニュートン反復の数、解の安定性、検出された分岐/イベントを印刷する
      * ケース 3: 分岐/イベントを特定するための二分法中の情報を印刷する
  * `linear_algo` 継続アルゴリズム `alg` のための線形ソルバーを設定します。例えば、`PALC` は拡張された問題（サイズ `n+1` の代わりに `n`）のための線形ソルバーが必要であり、したがって `contparams.newton_options.linsolver` に渡されるものを調整する必要があります。これは、`alg` の線形ソルバーを変更するための便利な引数であり、主に内部で使用されます。適切な方法は、正しい線形ソルバーを直接 `alg` に渡すことです。
  * `kind::AbstractContinuationKind` [内部] 継続の種類を説明するフラグ（平衡、コディメンション 2、...）。デフォルト = `EquilibriumCont()`

# 出力:

  * `contres::ContResult` 計算されたブランチを含む複合型。詳細は [`ContResult`](@ref) を参照してください。

!!! tip "反対方向にブランチを継続する"
    `ContinuationPar` の `ds` の符号を変更するだけです。


!!! tip "デバッグモード"
    デバッグモードを使用して、継続実行の進行状況に関するより多くの情報にアクセスします。例えば、反復ソルバーの収束、問題の更新など。

