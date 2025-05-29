```
struct RunSequential <: Iterable

RunSequential(;years)
```

E4STを順次実行します。`years`（または年のセット）を一つずつ実行します。最初のセットが設定の`config[:years]`と異なる場合は警告を出しながら`config[:years]`を上書きします。

  * `years = ["y2020", "y2025"]`: これはE4STを2回実行します。各年ごとに1回ずつ実行します。
  * `years = ["y2020", ["y2025", "y2030"]]`: これはE4STを2回実行します。`"y2020"`のために1回、`["y2025", "y2030"]`のために1回実行します。
