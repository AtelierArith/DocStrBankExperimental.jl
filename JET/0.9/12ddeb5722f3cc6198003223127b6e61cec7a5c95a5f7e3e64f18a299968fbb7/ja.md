```
@test_call [jetconfigs...] [broken=false] [skip=false] f(args...)
```

[`@report_call jetconfigs... f(args...)`](@ref @report_call) を実行し、関数呼び出し `f(args...)` が `@report_call` が検出できる問題から自由であることをテストします。テストが成功した場合は `Pass` 結果を返し、問題が検出された場合は `Fail` 結果を返し、予期しないエラーが発生した場合は `Error` 結果を返します。テストが `Fail` した場合、各問題の場所への抽象的なコールスタックが `stdout` に印刷されます。

```julia-repl
julia> @test_call sincos(10)
Test Passed
  Expression: #= none:1 =# JET.@test_call sincos(10)
```

[`@report_call`](@ref) と同様に、[一般的な設定](@ref) および [エラー分析特有の設定](@ref jetanalysis-config) をオプション引数として指定できます：

```julia-repl
julia> cond = false

julia> function f(n)
           # `cond` は型指定されておらず、サウンド分析パスによって報告されますが、
           # JET のデフォルト分析パスはそれを無視します
           if cond
               return sin(n)
           else
               return cos(n)
           end
       end;

julia> @test_call f(10)
Test Passed
  Expression: #= none:1 =# JET.@test_call f(10)

julia> @test_call mode=:sound f(10)
JET-test failed at none:1
  Expression: #= none:1 =# JET.@test_call mode = :sound f(10)
  ═════ 1 possible error found ═════
  ┌ @ none:2 goto %4 if not cond
  │ non-boolean (Any) used in boolean context: goto %4 if not cond
  └──────────

ERROR: テスト中にエラーが発生しました
```

`@test_call` は [`Test` 標準ライブラリ](https://docs.julialang.org/en/v1/stdlib/Test/)'s ユニットテストインフラストラクチャに完全に統合されています。これは、`@test_call` の結果が最終的な `@testset` サマリーに含まれ、`@test` マクロと同様に `skip` および `broken` 注釈をサポートすることを意味します：

```julia-repl
julia> using JET, Test

# Julia は型制約 `ref[]::Number` を `sin(ref[])` に伝播できないため、JET は `NoMethodError` を報告します
julia> f(ref) = isa(ref[], Number) ? sin(ref[]) : nothing;

# `ref[]` をローカル変数 `x` に抽出すれば、型安定にできます
julia> g(ref) = (x = ref[]; isa(x, Number) ? sin(x) : nothing);

julia> @testset "check errors" begin
           ref = Ref{Union{Nothing,Int}}(0)
           @test_call f(ref)             # fail
           @test_call g(ref)             # fail
           @test_call broken=true f(ref) # broken として注釈されるため、依然として "pass"
       end
check errors: JET-test failed at REPL[21]:3
  Expression: #= REPL[21]:3 =# JET.@test_call f(ref)
  ═════ 1 possible error found ═════
  ┌ f(ref::Base.RefValue{Union{Nothing, Int64}}) @ Main ./REPL[19]:1
  │ no matching method found `sin(::Nothing)` (1/2 union split): sin((ref::Base.RefValue{Union{Nothing, Int64}})[]::Union{Nothing, Int64})
  └────────────────────

Test Summary: | Pass  Fail  Broken  Total  Time
check errors  |    1     1       1      3  0.2s
ERROR: 一部のテストが通過しませんでした: 1 成功, 1 失敗, 0 エラー, 1 壊れた.
```
