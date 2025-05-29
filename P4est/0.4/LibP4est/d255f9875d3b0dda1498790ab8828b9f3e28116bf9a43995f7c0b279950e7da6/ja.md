```
sc_version()
```

libscのフルバージョンを返します。

### 戻り値

`VERSION_MAJOR.VERSION_MINOR.VERSION_POINT`の形式を使用してlibscのバージョンを返します。ここで、`VERSION_POINT`は追加のコミット数やgitコミットハッシュを示すためにドットや文字を含むことができます。

### プロトタイプ

```c
const char *sc_version (void);
```
