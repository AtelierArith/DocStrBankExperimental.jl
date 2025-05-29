```julia
abstract type OrderedSolution <: SymbolicPlanners.Solution
```

順序計画ソリューションのための抽象型です。`OrderedSolution`は反復インターフェースを満たす必要があります。順序ソリューションに対して`get_action(sol, t::Int)`を呼び出すと、ステップ`t`のための意図されたアクションが返されるべきです。
