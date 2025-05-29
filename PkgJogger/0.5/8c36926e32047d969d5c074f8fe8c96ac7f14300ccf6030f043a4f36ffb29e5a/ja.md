```
@test_benchmarks PkgName
```

`PkgName`のすべてのベンチマークを収集し、1回実行したときにエラーが発生しないことをテストします。

## 例

```julia-repl
julia> using PkgJogger, Example

julia> @test_benchmarks Example
│ テスト概要:  | 合格  合計
│ bench_timer.jl |    2      2
[...]
```

## テスト

各ベンチマークは`@testset`でラップされ、1回だけ実行され、エラーが発生しない場合に合格としてマークされます。これにより、ベンチマークスイートの迅速なスモークテストが提供され、実際にベンチマークを行う際に発生する調整、ウォームアップ、サンプル収集の通常のコストを回避します。

## ベンチマークの読み込み

テストのためのベンチマークの位置を特定することは、[`@jog`](@ref)と同じであり、[`PkgJogger.locate_benchmarks`](@ref)を使用して調べることができます。
