```
SparseOp(type::T,name::AbstractString, shape::NTuple{N,Int64}; kargs...) where{N,T}
```

は、その名前に基づいてスパース変換（`<: AbstractLinearOperator`）を生成します。

# 引数

  * `name::AbstractString`    - スパース変換の名前
  * `shape::NTuple{D,Int64}`  - 変換される配列のサイズ
  * (`kargs`)                 - 追加のキーワード引数
