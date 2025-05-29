```
FastDownward(
    search::String = "astar",
    heuristic::String = "add",
    h_params::Dict{String, String} = Dict(),
    max_time::Float64 = 300,
    verbose::Bool = false,
    log_stats::Bool = true,
    fd_path::String = get(ENV, "FD_PATH", ""),
    py_cmd::String = get(ENV, "PYTHON", "python")
)
```

FastDownwardプランニングシステムのラッパー[1]。このラッパーを使用するには、プランナーがローカルにインストールされている必要があります。オプションの詳細については、FastDownwardのドキュメントを参照してください。

[1] M. Helmert, "The Fast Downward Planning System," Journal of Artificial Intelligence Research, vol. 26, pp. 191–246, Jul. 2006, [https://doi.org/10.1613/jair.1705](https://doi.org/10.1613/jair.1705).

# 引数

  * `search`: 探索アルゴリズムを指定する文字列（例："astar", "ehc"）。
  * `heuristic`: 探索ヒューリスティックを指定する文字列（例："add", "lmcut"）。
  * `h_params`: 名前を値にマッピングする辞書としてのヒューリスティックパラメータ。
  * `max_time`: プランナーがタイムアウトする前の最大時間（秒）。
  * `verbose`: プランナーの出力を印刷するフラグ。
  * `log_stats`: 解の統計をログに記録するフラグ。
  * `fd_path`: `fast_downward.py`へのパス。
  * `py_cmd`: Python実行可能ファイルへのパス。
