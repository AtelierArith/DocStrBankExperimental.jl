```
sc_package_register(log_handler, log_threshold, name, full)
```

SCにソフトウェアパッケージを登録します。この関数は追加のスレッドが作成される前にのみ呼び出す必要があります。ロギングパラメータは[`sc_set_log_defaults`](@ref)と同様です。

### 戻り値

ユニークなパッケージIDを返します。

### プロトタイプ

```c
int sc_package_register (sc_log_handler_t log_handler, int log_threshold, const char *name, const char *full);
```
