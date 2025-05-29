```
sc_atol(nptr)
```

標準ライブラリのatol (3)関数の安全なバージョンです。

### パラメータ

  * `nptr`:[in] NUL終端文字列。

### 戻り値

変換された長整数値。無効な数値の場合は0。オーバーフロー時はLONG*MAX、アンダーフロー時はLONG*MIN。

### プロトタイプ

```c
long sc_atol (const char *nptr);
```
