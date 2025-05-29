```
StanProblem(model::BridgeStan.StanModel; nan_on_error::Bool=false)
```

データを持つ制約のないStanモデルのラッパーで、[LogDensityProblems](https://www.tamaspapp.eu/LogDensityProblems.jl/)インターフェースを実装しています。

`nan_on_error=true`の場合、Stanからのエラーは抑制され、`NaN`が返されます。
