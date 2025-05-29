```
run_threaded_scenarios(s::Scenarios, optimizer; remove_series=false)
```

REoptシナリオのバッチを`Scenarios.Nparallel`に従って並行して実行し、結果の辞書のベクターを返します。

`remove_series`が`true`の場合、すべての時系列結果が辞書から削除され、メモリ使用量が低く抑えられ、結果が長方形データストアと互換性を持つようになります。
