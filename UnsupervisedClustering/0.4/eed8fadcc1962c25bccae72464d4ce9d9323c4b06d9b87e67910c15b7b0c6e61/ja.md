```
MultiStart(
    local_search::AbstractAlgorithm
    verbose::Bool = DEFAULT_VERBOSE
    max_iterations::Integer = 200
)
```

MultiStartアプローチは、異なる初期点を持つ複数の解を生成するためにクラスタリングアルゴリズムを繰り返し適用し、最良の解を選択します。

# フィールド

  * `local_search`: 各メタヒューリスティックの反復で解を改善するために適用されるクラスタリングアルゴリズム。
  * `verbose`: アルゴリズムが実行中に追加情報を表示するかどうかを制御します。
  * `max_iterations`: アルゴリズムが停止する前に実行する最大反復回数を表します。
