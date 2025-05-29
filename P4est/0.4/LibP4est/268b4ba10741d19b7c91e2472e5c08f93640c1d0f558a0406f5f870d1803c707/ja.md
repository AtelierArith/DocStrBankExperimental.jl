```
p4est_version()
```

`p4est`の完全なバージョンを返します。

### 戻り値

`VERSION_MAJOR.VERSION_MINOR.VERSION_POINT`の形式を使用して`p4est`のバージョンを返します。ここで、`VERSION_POINT`は追加のコミット数やgitコミットハッシュを示すためにドットや文字を含むことができます。

### プロトタイプ

```c
const char *p4est_version (void);
```
