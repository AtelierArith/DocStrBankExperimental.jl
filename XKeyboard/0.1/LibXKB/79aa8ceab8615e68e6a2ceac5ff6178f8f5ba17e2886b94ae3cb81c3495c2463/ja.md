```
xkb_keymap_new_from_names(context, names, flags)
```

RMLVO名からキーマップを作成します。

主なキーマップエントリーポイント：RMLVO（ルール + モデル + レイアウト + バリアント + オプション）名のセットから新しいXKBキーマップを作成します。

### パラメータ

  * `context`: キーマップを作成するコンテキスト。
  * `names`: 使用するRMLVO名。[`xkb_rule_names`](@ref)を参照してください。
  * `flags`: キーマップのオプションフラグ、または0。

### 戻り値

RMLVO名に従ってコンパイルされたキーマップ、またはコンパイルに失敗した場合はNULL。

### 参照

[`xkb_rule_names`](@ref) xkb_keymap
