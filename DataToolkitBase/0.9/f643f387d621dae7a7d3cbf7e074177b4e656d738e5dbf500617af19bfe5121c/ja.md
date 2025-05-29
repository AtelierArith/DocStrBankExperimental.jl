```
CollectionVersionMismatch(version::Int)
```

現在操作中のコレクションの `version` は、現在の DataToolkitBase のバージョンではサポートされていません。

# 例の発生

```julia-repl
julia> fromspec(DataCollection, SmallDict{String, Any}("data_config_version" => -1))
ERROR: CollectionVersionMismatch: -1 (指定) ≠ 0 (現在)
  データコレクションの仕様は v-1 データコレクション形式を使用していますが、
  インストールされている DataToolkitBase バージョンは形式の v0 バージョンを期待しています。
  将来的には変換機能が実装される可能性がありますが、今のところは
  手動でファイルを v0 形式にアップグレードする必要があります。
Stacktrace: [...]
```
