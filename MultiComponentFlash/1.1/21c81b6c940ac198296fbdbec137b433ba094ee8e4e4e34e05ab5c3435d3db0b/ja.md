```
flash_2ph!(storage, K, eos, c, [V]; <キーワード引数>)
```

ストレージが事前に割り当てられている[`flash_2ph`](@ref)の非割り当てバージョン。

異なる条件で同じシステムの多くのフラッシュを実行する場合に便利です。

# 引数

  * `storage`: `flash_storage(eos, c, method = method)`からの出力である必要があります。事前に割り当てられたストレージ。

残りの引数は[`flash_2ph`](@ref)で文書化されています。

# キーワード引数

  * `update_forces = true`: ストレージ内の`p, T`依存の力を最初に更新します。
