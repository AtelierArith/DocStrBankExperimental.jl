```
xkb_keymap_new_from_file(context, file, format, flags)
```

キーマップファイルからキーマップを作成します。

ファイルには完全なキーマップが含まれている必要があります。たとえば、XKB*KEYMAP*FORMAT*TEXT*V1形式では、ファイルには1つのトップレベルの'xkb_keymap'セクションが含まれている必要があり、その中に他の必要なセクションが含まれています。

xkb_keymap

### パラメータ

  * `context`: キーマップを作成するコンテキスト。
  * `file`: コンパイルするキーマップファイル。
  * `format`: コンパイルするキーマップファイルのテキスト形式。
  * `flags`: キーマップのオプションフラグ、または0。

### 戻り値

指定されたXKBキーマップファイルからコンパイルされたキーマップ、またはコンパイルに失敗した場合はNULL。
