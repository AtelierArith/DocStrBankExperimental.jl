```
sc_array_memset(array, c)
```

配列ストレージにmemsetを実行します。memsetには文字をそのまま渡します。したがって、標準のmemset (3)と同様に、-1未満または127を超える値を設定する際には注意が必要です。

### パラメータ

  * `array`:[in,out] この配列のストレージは上書きされます。
  * `c`:[in] すべてのバイトを上書きする文字。

### プロトタイプ

```c
void sc_array_memset (sc_array_t * array, int c);
```
