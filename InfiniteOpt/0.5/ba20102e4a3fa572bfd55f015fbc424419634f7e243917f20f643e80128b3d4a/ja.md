```
map_reduced_cost(vref::GeneralVariableRef, key::Val{ext_key_name}, 
                  result::Int; kwargs...)
```

`vref`の削減コストを、拡張キー`key`によって区別される最適化モデルタイプの対応物にマップします。この定義は、`optimizer_model_variable`を容易に拡張できない再定式化拡張のためにのみ必要です。元の無限形式の変数間に直接的なマッピングがない再定式化のケースが該当します。それ以外の場合は、`optimizer_model_variable`がデフォルトでこれらのマッピングを行うために使用され、`kwargs`はこれらの関数に渡されます。ここで`result`は`value`で使用される結果インデックスです。
