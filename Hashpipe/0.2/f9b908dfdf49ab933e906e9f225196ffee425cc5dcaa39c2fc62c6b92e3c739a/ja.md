```
status_attach(instance_id::Int, p_status::Ref{status_t})
```

p_statusが指すHashpipeのステータスを、指定されたHashpipeインスタンスのステータス値で埋めます（存在しない場合は作成します）。

ロックセマフォもアタッチ/作成します。エラーの場合は非ゼロを返します。
