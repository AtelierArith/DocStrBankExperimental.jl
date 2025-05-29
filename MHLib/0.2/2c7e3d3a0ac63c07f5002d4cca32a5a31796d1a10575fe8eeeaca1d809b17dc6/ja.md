```
log_iteration(::Scheduler, method_name, obj_old, new_sol, new_incumbent, in_any_case,
    log_info)
```

イテレーションログ情報を書き込みます。

`in_any_case`が設定されている場合、または`params.lfreq`と`params.lnewinc`に依存して行が書き込まれます。`method_name`: 適用されたメソッドの名前または "-"（初期に与えられた解の場合）；`obj_old`: 最後のオペレーターを適用する前の目的値；`param new_sol`: 新しく作成された解；`new_incumbent`: メソッドが新しいインカンベント解を生成した場合はtrue；`in_any_case`: イテレーションログのフィルタリングをオフにします；`log_info`: 空でない場合にオプションで追加されるカスタマイズされたログ情報。
