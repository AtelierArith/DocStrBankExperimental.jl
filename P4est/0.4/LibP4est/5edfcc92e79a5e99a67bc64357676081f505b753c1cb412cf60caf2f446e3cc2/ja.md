```
sc_log(filename, lineno, package, category, priority, msg)
```

すべてのパッケージによって呼び出される中央ログ関数。パッケージによってログ呼び出しをディスパッチし、カテゴリと優先度でフィルタリングします。

### パラメータ

  * `package`:[in] 登録されたパッケージIDである必要があります。-1も可。
  * `category`:[in] `SC_LC_NORMAL`または`SC_LC_GLOBAL`である必要があります。
  * `priority`:[in] `SC_LP_ALWAYS`より大きく、`SC_LP_SILENT`より小さい必要があります。

### プロトタイプ

```c
void sc_log (const char *filename, int lineno, int package, int category, int priority, const char *msg);
```
