```
prettify(ex; kw...)
```

与えられた式を整形し、すべての `LineNumberNode` と余分なコードブロックを削除します。

# オプション (Kwargs)

すべてのオプションはデフォルトで `true` です。

  * `rm_lineinfo`: `LineNumberNode` を削除します。
  * `flatten_blocks`: `begin ... end` コードブロックをフラットにします。
  * `rm_nothing`: `begin ... end` 内の `nothing` を削除します。
  * `preserve_last_nothing`: `begin ... end` 内の最後の `nothing` を保持します。
  * `rm_single_block`: 単一の `begin ... end` を削除します。
  * `alias_gensym`: `##<name>#<num>` を `<name>_<id>` に置き換えます。
  * `renumber_gensym`: gensym ID の番号を再割り当てします。

!!! tips
    マクロ呼び出し内の `LineNumberNode` は削除されません。なぜなら、`macrocall` 式は `LineNumberNode` を必要とするからです。詳細は [issues/#9](https://github.com/Roger-luo/Expronicon.jl/issues/9) を参照してください。

