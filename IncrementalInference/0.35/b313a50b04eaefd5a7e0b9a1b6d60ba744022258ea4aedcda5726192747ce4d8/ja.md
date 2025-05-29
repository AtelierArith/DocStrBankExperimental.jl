```julia
fetchCliqHistoryAll!(smt)
fetchCliqHistoryAll!(smt, hist)

```

非同期タスクを完了したクリーク状態マシンからソルバの履歴を取得し、`hist::Dict{Int,Tuple}` 辞書に格納します。
