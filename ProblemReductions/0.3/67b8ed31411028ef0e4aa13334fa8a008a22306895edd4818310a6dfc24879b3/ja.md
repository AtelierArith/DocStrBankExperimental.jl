```
solution_size(problem::AbstractProblem, config) -> SolutionSize
```

与えられた構成 `config` に対する `problem` のサイズ。複数の構成がある場合は、パフォーマンス向上のために `ProblemReductions.solution_size_multiple` を代わりに使用してください。
