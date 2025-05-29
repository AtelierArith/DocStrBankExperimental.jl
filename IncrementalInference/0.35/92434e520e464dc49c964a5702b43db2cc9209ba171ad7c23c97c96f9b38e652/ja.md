```julia
animateCliqStateMachines(tree, cliqsyms, hists; frames)

```

`cliqsyms::Vector{Symbol}`のための時間同期状態機械イベントを表す多くの画像を'/tmp/?/csm_%d.png'に描画します。

ノート

  * 状態履歴は以前に記録されている必要があります（ツリーのクリークに保存されています）。

関連

printCliqHistorySummary
