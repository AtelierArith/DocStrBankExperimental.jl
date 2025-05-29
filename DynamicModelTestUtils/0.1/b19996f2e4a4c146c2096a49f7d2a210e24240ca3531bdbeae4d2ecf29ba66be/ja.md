```
test_instantaneous(sys::ModelingToolkit.AbstractSystem,
    ic,
    checks::Union{Num, Array};
    t = nothing)
```

`test_instantaneous` は、特定の条件で `ODEProblem` を構築し実行するためのヘルパーラッパーです。これは、MTKモデルの基本的な整合性チェックに使用することを意図しており、例えば、特定の条件での導関数が正しい符号を持つことを確認するために使用されます。システム、ODEProblemコンストラクタに渡す初期条件辞書（パラメータを含む）、およびODEProblemから抽出するシステムの観測可能な値のリストを渡す必要があります。`checks` が単一の `Num` の場合、結果はその観測値になります。それ以外の場合は、提供されたチェックと同じ順序の配列が返されます。
