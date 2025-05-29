```julia
ContinueFixedPoint!(fileName::String, F::T, Update::R) where {T<:Function, R<:Function}
```

JLD2ファイル`fileName`に保存されたチェックポイントから再構築された`SelfCons`に対して固定点反復を再実行します。
