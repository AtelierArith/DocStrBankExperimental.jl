```julia
struct CheapStack{T}
```

シンプルなスタックコンテナ。

# 機能

以下の操作がサポートされています：

  * `isempty`
  * `empty!`
  * `first`
  * `length`
  * `pop!`
  * `push!`

便利のために、`CheapStack`は[イテレーションインターフェース](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration)を実装しています。

# フィールド

  * `store::UnsafeArrays.UnsafeArray{T, 1} where T`
  * `ptr::Base.RefValue{Int64}`
