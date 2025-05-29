```
Highs_getStringOptionValue(highs, option, value)
```

文字列値のオプションを取得します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `option`: オプションの名前。
  * `value`: オプションの現在の値を格納するために確保されたメモリへのポインタ（少なくとも `kMaximumStringLength` のサイズ）。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
