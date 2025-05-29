```julia
repeatCSMStep!(hist, step; duplicate, enableLogging)

```

ソルバー状態機械ステップを繰り返す – デバッグに便利です。

ノート

  * `solveTree!(fg, recordcliqs=[:0; :x7; ...])` と組み合わせて使用 – すなわち、クリックスフロンタルを識別子として使用します。

      * すべてを記録するには、`recordcliqs=ls(fg)` を使用できます。
  * `duplicate` は、`hists` の履歴やプライムデータを変更しないようにします。
  * 古いAPI `sandboxCliqResolveStep` を置き換えます。
  * [Revise.jl](https://github.com/timholy/Revise.jl) のようなツールと組み合わせて使用することを検討してください。

      * VSCodeではデフォルトでオンになっています。
  * 内部的に `csmc.enableLogging=false` を設定します。

例

```julia
using IncrementalInference

# ファクターグラフを生成
fg = generateGraph_Kaess()

# 解決し、すべてを記録
smtasks = Task[]
tree, _, = solveTree!(fg, smtasks=smtasks, recordcliqs=ls(fg));
# graphviz と xdot がインストールされている場合、ベイズツリーを描画
drawTree(tree, show=true)

# 履歴を取得
hists = fetchCliqHistoryAll!(smtasks);

# ステップ2の前に新しいcsmcを確認
csmc_ = repeatCSMStep!(hists, 1, 1)

# VSCodeデバッグ用
@enter repeatCSMStep!(hists, 1, 1)

# あるいは、より長い変更のチェーンをテストする
hists_ = deepcopy(hists)
repeatCSMStep!(hists_, 1, 4, duplicate=false)
repeatCSMStep!(hists_, 1, 5, duplicate=false)
repeatCSMStep!(hists_, 1, 6, duplicate=false)
```

DevNotes

  * TODO: `FSM.sandboxStateMachineStep` と統合する

関連

[`solveTree!`](@ref), [`solveCliqUp!`](@ref), [`fetchCliqHistoryAll`](@ref), [`printCSMHistoryLogical`](@ref), [`printCSMHistorySequential`](@ref), cliqHistFilterTransitions
