```
StoppingCriterion
```

停止基準を表すファンクタのための抽象型であり、呼び出し可能な構造体です。命名規則は関数に従っており、例えば [`StopAfterIteration`](@ref) を参照してください。

すべての StoppingCriterion はコンストラクタを提供し、その関数はインターフェース `(p,o,i)` を持たなければなりません。ここで、[`AbstractManoptProblem`](@ref) と [`AbstractManoptSolverState`](@ref) および現在の反復回数が引数となり、停止するかどうかの真偽値を返します。

デフォルトでは、各 `StoppingCriterion` は基準が満たされたときに詳細を提供するためのフィールド `reason` を提供する必要があります（それ以外の場合は空です）。
