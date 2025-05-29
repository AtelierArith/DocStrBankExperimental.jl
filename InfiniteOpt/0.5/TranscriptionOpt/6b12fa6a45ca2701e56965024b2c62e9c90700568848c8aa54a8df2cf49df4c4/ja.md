```
TranscriptionModel([optimizer_constructor;
                   caching_mode::MOIU.CachingOptimizerMode = MOIU.AUTOMATIC,
                   bridge_constraints::Bool = true])::JuMP.Model
```

`TranscriptionData`を`ext`データフィールドに含む`JuMP.Model`を返します。通常のJuMP `Model`と同じ引数を受け取ります。詳細な変数および制約の命名は`verbose_naming`を介して有効にできます。

**例**

```julia-repl
julia> TranscriptionModel()
A JuMP Model
Feasibility problem with:
Variables: 0
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.
```
