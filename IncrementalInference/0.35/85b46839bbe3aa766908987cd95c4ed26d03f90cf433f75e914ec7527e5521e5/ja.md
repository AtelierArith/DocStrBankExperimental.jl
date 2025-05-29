```julia
solveTree!(dfgl; ...)
solveTree!(
    dfgl,
    oldtree;
    timeout,
    storeOld,
    verbose,
    verbosefid,
    delaycliqs,
    recordcliqs,
    limititercliqs,
    injectDelayBefore,
    skipcliqids,
    eliminationOrder,
    eliminationConstraints,
    smtasks,
    dotreedraw,
    runtaskmonitor,
    algorithm,
    solveKey,
    multithread
)

```

`opt::SolverParams`およびキーワード引数に従ってベイズツリー上で推論を実行します。

ノート

  * `solveGraph!`とエイリアスされています。
  * 固定遅延解法を含むさまざまなオプションがあります - 詳細は`getSolverParams(fg)`を参照してください。

      * 詳細についてはオンラインドキュメントを参照してください: https://juliarobotics.org/Caesar.jl/latest/
  * 最新の結果は常に`solvekey=:default`に保存されます。
  * 実験的な`storeOld::Bool=true`は、現在の結果をスーパソルブ`：default_k`として複製します。

      * `solvable==1`の仮定に基づいています。
  * `limititercliqs`は、特定のCSMが行う反復の数を制限することをユーザーに許可します。
  * キーワード`verbose`および`verbosefid::IOStream`は、出力をファイルまたはデフォルトの`stdout`に送信するために一緒に使用できます。
  * キーワード`recordcliqs=[:x0; :x7...]`は、どのクリックステップを記録するかを前面で識別します。

      * [`repeatCSMStep!`](@ref)、[`printCSMHistoryLogical`](@ref)、[`printCSMHistorySequential`](@ref)を参照してください。

DevNotes

  * TODO キーワード引数を新しい@parameter `SolverOptions`型に変更します。

例

```julia
# 古い`tree`を渡して計算のリサイクリングを有効にします -- 詳細はオンラインドキュメントを参照してください
tree = solveTree!(fg [,tree])
```

関連

`solveGraph!`、[`solveCliqUp!`](@ref)、[`solveCliqDown!`](@ref)、[`buildTreeReset!`](@ref)、[`repeatCSMStep`](@ref)、[`printCSMHistoryLogical`](@ref)
