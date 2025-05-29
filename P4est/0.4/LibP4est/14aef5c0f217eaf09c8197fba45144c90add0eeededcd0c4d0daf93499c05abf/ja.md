```
sc_set_log_defaults(log_stream, log_handler, log_thresold)
```

SCログのデフォルト動作を制御します。

### パラメータ

  * `log_stream`:[in] `sc_logf`で使用するストリームを設定します（またはstdoutの場合はNULL）。
  * `log_handler`:[in] デフォルトのSCログハンドラを設定します（NULLは組み込みを選択します）。
  * `log_threshold`:[in] デフォルトのSCログ閾値を設定します（または`SC_LP_DEFAULT`）。`SC_LP_ALWAYS`または`SC_LP_SILENT`である可能性があります。

### プロトタイプ

```c
void sc_set_log_defaults (FILE * log_stream, sc_log_handler_t log_handler, int log_thresold);
```
