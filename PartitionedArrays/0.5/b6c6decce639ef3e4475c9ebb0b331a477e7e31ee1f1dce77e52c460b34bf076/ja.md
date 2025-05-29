```
OwnAndGhostIndices
```

所有インデックスとゴーストインデックスを別々に保存するためのコンテナ。ローカルインデックスは、所有インデックスとゴーストインデックスを連結することによって定義されます。

# プロパティ

  * `own::OwnIndices`: 所有インデックスのためのコンテナ。
  * `ghost::GhostIndices`: ゴーストインデックスのためのコンテナ。
  * `global_to_owner`: [オプション: `nothing` である可能性があります] 各グローバルIDの所有者を含むベクター。

# スーパタイプ階層

```
OwnAndGhostIndices{A} <: AbstractLocalIndices
```

ここで `A=typeof(global_to_owner)` です。
