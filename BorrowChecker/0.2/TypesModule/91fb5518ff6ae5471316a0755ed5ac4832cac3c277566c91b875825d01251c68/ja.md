```
OwnedMut{T} <: AbstractOwned{T}
```

可変の所有値。一般的な操作：

  * `@own :mut x = value` を使用して作成
  * `@take!` (移動) または `@take` (コピー) を使用して値にアクセス
  * setproperty! または setindex! によって修正: `x.field = value` または `x[indices...] = value`
  * `@ref` または `@ref :mut` を使用して借用
  * `.field` または `[indices...]` を介してフィールド/インデックスにアクセス (LazyAccessor を返す)

一度移動されると、その値には再度アクセスできません。

# 内部フィールド (公開 API の一部ではありません):

  * `value::T`: 含まれている値
  * `moved::Bool`: 値が移動されたかどうか
  * `immutable_borrows::Int`: アクティブな不変借用のカウント
  * `mutable_borrows::Int`: アクティブな可変借用のカウント
  * `symbol::Symbol`: エラーレポート用の変数名
