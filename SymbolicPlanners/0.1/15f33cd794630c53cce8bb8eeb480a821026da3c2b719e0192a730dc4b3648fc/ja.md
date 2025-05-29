```
Pyperplan(
    search::String = "astar",
    heuristic::String = "add",
    log_level::String = "info",
    log_stats::Bool = true,
    max_time::Float64 = 300,
    verbose::Bool = false,
    py_cmd::String = get(ENV, "PYTHON", "python")
)
```

Pyperplan軽量STRIPSプランナーのラッパー[1]。このラッパーを使用するには、プランナーをローカルにインストールする必要があります。オプションの詳細については、Pyperplanのドキュメントを参照してください。

[1] Y. Alkhazraji et al., "Pyperplan." Zenodo, 2020. [https://doi.org/10.5281/zenodo.3700819](https://doi.org/10.5281/zenodo.3700819).

# 引数

  * `search`: 探索アルゴリズムを指定する文字列（例："astar", "gbf"）。
  * `heuristic`: 探索ヒューリスティックを指定する文字列（例："hadd", "hmax"）。
  * `log_level`: プランナーを実行する際にログに記録する情報の量。
  * `log_stats`: 解決統計をログに記録するフラグ。
  * `max_time`: プランナーがタイムアウトするまでの最大時間（秒）。
  * `verbose`: プランナーの出力を印刷するフラグ。
  * `py_cmd`: Python実行可能ファイルへのパス。
