```
Borrowed{T,O<:AbstractOwned} <: AbstractBorrowed{T}
```

所有された値への不変参照。一般的な操作：

  * `@ref lt x = value` を使用して作成
  * `@take` を使用して値にアクセス（コピー）
  * `.field` または `[indices...]` を介してフィールド/インデックスにアクセス（LazyAccessorを返す）

複数の不変参照が同時に存在することができます。参照はそのライフタイムスコープ内でのみ有効です。

# 内部フィールド（公開APIの一部ではありません）：

  * `value::T`: 参照された値
  * `owner::O`: 元の所有された値
  * `lifetime::Lifetime`: この参照が有効なスコープ
  * `symbol::Symbol`: エラーレポート用の変数名
