```
BorrowedMut{T,O<:OwnedMut} <: AbstractBorrowed{T}
```

所有された値への可変参照。一般的な操作：

  * `@ref lt :mut x = value` を使用して作成
  * `@take` を使用して値にアクセス（コピー）
  * `.field` または `[indices...]` を介してフィールド/インデックスにアクセス（LazyAccessorを返す）

同時に存在できる可変参照は1つだけで、同時に不変参照は存在できません。

# 内部フィールド（公開APIの一部ではありません）：

  * `value::T`: 参照された値
  * `owner::O`: 元の所有された値
  * `lifetime::Lifetime`: この参照が有効なスコープ
  * `symbol::Symbol`: エラーレポート用の変数名
