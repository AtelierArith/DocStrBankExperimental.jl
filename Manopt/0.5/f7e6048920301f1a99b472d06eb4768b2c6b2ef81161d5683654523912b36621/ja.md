```
ステップサイズ
```

ステップサイズを表すファンクタのための抽象型です。これらは呼び出し可能な構造体です。命名規則は `TypeOfStepSize` で、例えば `ConstantStepsize` です。

すべてのステップサイズはコンストラクタを提供し、その関数はインターフェース `(p,o,i)` を持たなければなりません。ここで、[`AbstractManoptProblem`](@ref) と [`AbstractManoptSolverState`](@ref) および現在の反復回数が引数となり、使用するステップサイズの数値を返します。

ほとんどの場合、[`ManifoldDefaultsFactory`](@ref) を使用することが推奨されます。その後、ファクトリを作成する関数は `TypeOf` と呼ばれるべきか、もしそれが混乱を招くかあまりにも一般的であれば `TypeOfLength` と呼ばれるべきです。

# 参照

[`Linesearch`](@ref)
