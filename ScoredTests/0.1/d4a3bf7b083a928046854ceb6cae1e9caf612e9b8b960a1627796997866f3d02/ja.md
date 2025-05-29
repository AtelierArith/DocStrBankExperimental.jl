```
@scoredtest expr [name=""] [award=DefaultScoring.award] [penalty=DefaultScoring.penalty] -> ScoredTests.ScoredTest
@scoredtest(expr[, name="", award=DefaultScoring.award, penalty=DefaultScoring.penalty]) -> ScoredTests.ScoredTest
```

ブール `expr` を評価し、[`ScoredTest`](@ref) を返します。`expr` が `Bool` 以外を返すと [`ScoredTests.ScoredTestException`](@ref) をスローします。

[`ScoredTest`](@ref) には `name`（文字列であるべき）、`award` および `penalty`（*正* の `Real` であるべき）が含まれます。

[`ScoredTest`](@ref) は次のようになります。

  * 合格: `expr` が `true` の場合、テストは `award` を与えます。
  * 不合格: `expr` が `false` の場合、テストは `penalty` を取ります。
  * エラー: `expr` がエラーをスローした場合、テストは `penalty` を取ります。

テストの状態は [`ScoredTests.ispass`](@ref)、[`ScoredTests.isfail`](@ref)、および [`ScoredTests.iserror`](@ref) で確認できます。

達成されたスコアは [`ScoredTests.score`](@ref) でアクセスできます。

# 例

```julia-repl
julia> st = @scoredtest π < 3 award=2 penalty=4;

julia> ScoredTests.ispass(st)
false

julia> ScoredTests.isfail(st)
true

julia> ScoredTests.iserror(st)
false

julia> ScoredTests.score(st)
-4
```
