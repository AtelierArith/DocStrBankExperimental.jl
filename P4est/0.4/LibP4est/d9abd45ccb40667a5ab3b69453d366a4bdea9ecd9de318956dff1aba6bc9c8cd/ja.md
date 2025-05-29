```
p4est_init(log_handler, log_threshold)
```

`p4est`をSCライブラリに登録し、ログの動作を設定します。この関数はオプションです。この関数は追加のスレッドが作成される前にのみ呼び出す必要があります。この関数が呼び出されない場合、またはlog*handlerがNULLの場合、デフォルトのSCログハンドラーが使用されます。この関数が呼び出されない場合、またはlog*thresholdが`SC_LP_DEFAULT`の場合、デフォルトのSCログ閾値が使用されます。デフォルトのSCログ設定は[`sc_set_log_defaults`](@ref) ()を使用して変更できます。

### プロトタイプ

```c
void p4est_init (sc_log_handler_t log_handler, int log_threshold);
```
