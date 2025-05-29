```
Data(my_data; stop_when_exhausted=false)
```

イテレーション制御、例えば `Data(rand(100))` のように。

この制御の各適用で、イテラブル `data` から新しい `item` が取得され（`iterate` を使用）、`IterationControl.ingest!(m, item)` が呼び出されます。ここで `m` はイテレートされているオブジェクトです。

制御は、`data` イテラブルが完了すると受動的になります。制御の受動的な適用の後に停止をトリガーするには、`stop_when_exhausted=true` を設定します。
