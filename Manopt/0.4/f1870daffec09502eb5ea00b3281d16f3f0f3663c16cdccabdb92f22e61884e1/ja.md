```
ステップサイズ
```

ステップサイズを表すファンクタのための抽象型です。これらは呼び出し可能な構造体です。命名規則は `TypeOfStepSize` で、例えば `ConstantStepsize` です。

すべてのステップサイズはコンストラクタを提供し、その関数はインターフェース `(p,o,i)` を持たなければなりません。ここで、[`AbstractManoptProblem`](@ref) と [`AbstractManoptSolverState`](@ref) および現在の反復回数が引数となり、使用するステップサイズである数値を返します。

# 参照

[`Linesearch`](@ref)
