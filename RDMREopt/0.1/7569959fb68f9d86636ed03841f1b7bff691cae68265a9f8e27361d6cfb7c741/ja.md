```
run_serial_scenarios(s::Scenarios, optimizer; remove_series=false)
```

REoptシナリオをforループで1つずつ実行し、結果の辞書のベクトルを返します。

`remove_series`が`true`の場合、すべての時間系列結果が辞書から削除され、メモリ使用量が低く抑えられ、結果が長方形データストアと互換性を持つようになります。
