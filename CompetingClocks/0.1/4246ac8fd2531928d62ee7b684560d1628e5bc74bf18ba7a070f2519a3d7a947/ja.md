```
DebugWatcher()
```

デバッグのためには、シミュレーションの可視性が重要です。このウォッチャーは、すべての有効または無効にされたものを、すべての有効とすべての無効のリストとして記録します。これは完全なイベント履歴であり、今後のプロセスのフィルタリングと考えることができます。

```
watcher = DebugWatcher{String}()
# いくつかのものを有効および無効にします。
(watcher.enabled[1].clock,
watcher.enabled[1].distribution,
watcher.enabled[1].te,
watcher.enabled[1].when)
```
