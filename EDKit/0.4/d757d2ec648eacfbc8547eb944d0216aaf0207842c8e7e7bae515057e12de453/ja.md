```
operator(mats::AbstractVector{<:AbstractMatrix}, inds::AbstractVector{<:AbstractVector}, B::AbstractBasis)
```

`Operator`のコンストラクタ。

## 入力:

  * `mats`: ローカルオペレーターの行列のリスト。
  * `inds`: ローカルオペレーターが作用するサイトのリスト。
  * `B`   : 基底。

## 出力:

  * `O` : オペレーター。
