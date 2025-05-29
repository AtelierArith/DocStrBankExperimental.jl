```
run_checkset(data, checkset::CheckSet; threaded::Bool=false)::CheckSummary
```

提供されたデータに対して完全な検証チェックセットを実行します。

指定されたCheckSet内のすべてのチェックを実行し、逐次または並列実行のオプションがあります。

# 引数

  * `data`: 検証されるデータセット（Tables.jlインターフェースをサポートしている必要があります）
  * `checkset::CheckSet`: 実行されるチェックのコレクション
  * `threaded::Bool`: チェックを並列で実行するかどうか（デフォルト: false）

# 戻り値

次の内容を含む`CheckSummary`:

  * チェックセットの名前
  * 各チェックの結果
  * 総実行時間

# 例

```julia
summary = run_checkset(dataset, payment_checks, threaded=true)
```
