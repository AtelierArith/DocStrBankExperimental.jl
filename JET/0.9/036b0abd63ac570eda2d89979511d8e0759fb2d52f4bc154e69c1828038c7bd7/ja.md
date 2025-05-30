```
@test_opt [jetconfigs...] [broken=false] [skip=false] f(args...)
```

[`@report_opt jetconfigs... f(args...)`](@ref @report_opt) を実行し、関数呼び出し `f(args...)` が `@report_opt` が検出できる最適化の失敗や未解決のメソッドディスパッチから自由であることをテストします。

[`@report_opt`](@ref) と同様に、[一般的な設定](@ref) および [最適化分析特有の設定](@ref optanalysis-config) をオプション引数として指定できます：

```julia-repl
julia> function f(n)
            r = sincos(n)
            # `println` はランタイムディスパッチが多いですが、
            # `target_modules` 設定を使って `Base` からの対応するレポートを無視できます
            println(r)
            return r
       end;

julia> @test_opt target_modules=(@__MODULE__,) f(10)
Test Passed
  Expression: #= REPL[3]:1 =# JET.@test_call analyzer = JET.OptAnalyzer target_modules = (#= REPL[3]:1 =# @__MODULE__(),) f(10)
```

[`@test_call`](@ref) と同様に、`@test_opt` は [`Test` 標準ライブラリ](https://docs.julialang.org/en/v1/stdlib/Test/) と完全に統合されています。詳細については [`@test_call`](@ref) を参照してください。
