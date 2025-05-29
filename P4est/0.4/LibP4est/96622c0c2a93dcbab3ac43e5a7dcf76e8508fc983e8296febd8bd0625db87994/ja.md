```
sc_atoi(nptr)
```

標準ライブラリの atoi (3) 関数の安全なバージョンです。

### パラメータ

  * `nptr`:[in] NUL で終わる文字列。

### 戻り値

変換された整数値。無効な数値の場合は 0。オーバーフロー時は INT*MAX、アンダーフロー時は INT*MIN。

### プロトタイプ

```c
int sc_atoi (const char *nptr);
```
