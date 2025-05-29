```
CalibrationProblem(problem; kwargs...)
```

既存の `problem` から新しいキャリブレーション問題を構築しますが、新しいキーワード引数 `kwargs` を指定します。指定されていないキーワード引数はデフォルトに戻りますが、`p0` は `solution(problem)` に戻ります。
