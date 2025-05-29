```
map_value([ref/expr], key::Val{ext_key_name}, result::Int; kwargs...)
```

`ref`の値を、拡張キー`key`によって区別される最適化モデルタイプの対応するものにマップします。この`key`は`Val{ext_key_name}`型です。ここで`ref`は、変数参照と制約参照の両方のメソッドを参照する必要があります。これは、`optimizer_model_variable`、`optimizer_model_expression`、および/または`optimizer_model_constraint`を容易に拡張できない再定式化拡張のためにのみ定義する必要があります。元の無限形式において変数と/または制約の間に直接的なマッピングがない再定式化のケースが該当します。それ以外の場合、`optimizer_model_variable`、`optimizer_model_expression`、および`optimizer_model_constraint`がデフォルトでこれらのマッピングを行うために使用され、`kwargs`はこれらの関数に渡されます。ここで`result`は`value`で使用される結果インデックスです。
