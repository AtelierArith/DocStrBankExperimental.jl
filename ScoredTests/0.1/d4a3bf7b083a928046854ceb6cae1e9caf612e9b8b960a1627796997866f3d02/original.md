```
@scoredtest expr [name=""] [award=DefaultScoring.award] [penalty=DefaultScoring.penalty] -> ScoredTests.ScoredTest
@scoredtest(expr[, name="", award=DefaultScoring.award, penalty=DefaultScoring.penalty]) -> ScoredTests.ScoredTest
```

Evaluates boolean `expr`ession and returns [`ScoredTest`](@ref), throws [`ScoredTests.ScoredTestException`](@ref) when `expr` returns not `Bool`.

[`ScoredTest`](@ref) has `name` (should be string), `award` and `penalty` (should be *positive* `Real`s).

A [`ScoredTest`](@ref) can be

  * Passed: `expr` is `true`, test gives `award`;
  * Failed: `expr` is `false`, test takes `penalty`;
  * Errored: `expr` throws error, test takes `penalty`.

Status of test can be checked by [`ScoredTests.ispass`](@ref), [`ScoredTests.isfail`](@ref) and [`ScoredTests.iserror`](@ref).

Achived score accesible by [`ScoredTests.score`](@ref).

# Example

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
