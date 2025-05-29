```
map_optimizer_index(ref, key::Val{ext_key_name}; kwargs...)
```

`ref`の`MathOptInterface`インデックスを、拡張キー`key`によって区別される最適化モデルタイプの対応するインデックスにマッピングします。ここで`ref`は、変数参照と制約参照の両方のメソッドを参照する必要があります。これは、`optimizer_model_variable`および`optimizer_model_constraint`を容易に拡張できない再定式化拡張のためにのみ定義する必要があります。元の無限形式において変数と/または制約の間に直接的なマッピングがない再定式化のケースが該当します。そうでなければ、デフォルトで`optimizer_model_variable`および`optimizer_model_constraint`がこれらのマッピングを行うために使用され、`kwargs`も渡されます。
