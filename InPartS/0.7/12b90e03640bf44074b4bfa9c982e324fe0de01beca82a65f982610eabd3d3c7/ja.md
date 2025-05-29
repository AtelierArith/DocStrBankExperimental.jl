```
BurstModeCallback(; interval, affect, maxcount=10, trigger_offset=0.0, trigger_interval=10.0) <: AbstractCallback
```

`affect`を`trigger_offset`と`trigger_interval`で初期化された`PeriodicCallback`によってトリガーされた後、合計`maxcount`回の反復のために、`interval`時間単位ごとに実行するコールバックを返します。

## 例

次のように作成されたコールバック

```
BurstModeCallback(; interval=0.1,
                        affect=printcurrenttime,
                        maxcount=3,)
```

`printcurrenttime`があなたが思っていることを行う場合、シミュレーション中に`0.0, 0.1, 0.2, 10.0, 10.1, 10.2, 20.0, ...`を印刷します。
