```
xkb_keysym_get_name(keysym, buffer, size)
```

keysymの名前を取得します。

keysymsの命名方法については、xkb*keysym*tを参照してください。

!!! warning
    渡されたバッファが小さすぎる場合、文字列は切り捨てられます（ただし、NULで終端されています）；少なくとも64バイトのサイズを推奨します。


切り捨てが発生したかどうかは、戻り値とバッファの長さを比較することで確認できます。これはsnprintf(3)関数に似ています。

### パラメータ

  * `keysym`:[in] keysym。
  * `buffer`:[out] 名前を書き込むための文字列バッファ。
  * `size`:[in] バッファのサイズ。

### 戻り値

NULバイトを除いた名前のバイト数。keysymが無効な場合は-1を返します。

### 参照

[`xkb_keysym_t`](@ref)
