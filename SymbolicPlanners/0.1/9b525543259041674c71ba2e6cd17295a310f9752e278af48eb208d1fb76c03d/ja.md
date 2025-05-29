```
ENHSP(
    search::String = "astar",
    heuristic::String = "add",
    h_mult::Float64 = 1.0,
    log_stats::Bool = true,
    max_time::Float64 = 300,
    verbose::Bool = false,
    enhsp_path::String = get(ENV, "ENHSP_PATH", ""),
    java_cmd::String = get(ENV, "JAVA", "java")
)
```

Expressive Numeric Heuristic Search Planner (ENHSP) [1] のラッパーです。このラッパーを使用するには、プランナーがローカルにインストールされている必要があります。オプションの詳細については、ENHSP のドキュメントを参照してください。

[1] E. Scala et al., "ENHSP", [https://sites.google.com/view/enhsp/](https://sites.google.com/view/enhsp/).

# 引数

  * `search`: 検索アルゴリズムを指定する文字列（例："gbfs", "WAStar"）。
  * `heuristic`: 検索ヒューリスティックを指定する文字列（例："hadd", "aibr"）。
  * `h_mult`: 重み付き A* のためのヒューリスティック乗数。
  * `log_stats`: 解決統計をログに記録するフラグ。
  * `max_time`: プランナーがタイムアウトするまでの最大時間（秒）。
  * `verbose`: プランナーの出力を印刷するフラグ。
  * `enhsp_path`: `enhsp.jar` へのパス。
  * `java_cmd`: Java 実行可能ファイルへのパス。
