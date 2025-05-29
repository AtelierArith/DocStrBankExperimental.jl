```
sc_strcopy(dest, size, src)
```

文字列コピー関数を提供します。

### パラメータ

  * `dest`:[out] 長さが少なくとも *size* のバッファ。出力時、NULLまたは*size* == 0の場合は変更されません。
  * `size`:[in] *dest* の割り当て長。
  * `src`:[in] NULL終端文字列。

### 戻り値

sc_snprintf (dest, size, "s", src) と同等です。

### プロトタイプ

```c
void sc_strcopy (char *dest, size_t size, const char *src);
```
