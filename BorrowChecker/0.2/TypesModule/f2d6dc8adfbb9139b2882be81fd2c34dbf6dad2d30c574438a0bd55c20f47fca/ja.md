```
Owned{T} <: AbstractOwned{T}
```

不変の所有値。一般的な操作：

  * `@own x = value` を使用して作成
  * `@take!` (移動) または `@take` (コピー) を使用して値にアクセス
  * `@ref` を使用して借用
  * `.field` または `[indices...]` を介してフィールド/インデックスにアクセス (LazyAccessorを返す)

一度移動されると、その値には再度アクセスできません。

# 内部フィールド (公開APIの一部ではありません):

  * `value::T`: 含まれる値
  * `moved::Bool`: 値が移動されたかどうか
  * `immutable_borrows::Int`: アクティブな不変借用のカウント
  * `symbol::Symbol`: エラーレポート用の変数名
