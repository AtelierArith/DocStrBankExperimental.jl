```
benchmark_result(trial::BenchmarkTools.Trial)
```

`BenchmarkTool.@benchmark` の実行から得られる最小時間と割り当ての結果を含む短い文字列です。

テストケースで次のように使用できます：

```
trial = @benchmark myfunc($x, $y)
@test_result benchmark_result(trial)
```
