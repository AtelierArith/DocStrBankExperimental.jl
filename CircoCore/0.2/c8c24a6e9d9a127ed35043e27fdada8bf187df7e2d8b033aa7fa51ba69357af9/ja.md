```
OnBecome(reincarnation::Actor)
```

アクターのライフサイクルメッセージで、`become()`アクションを示します。

`reincarnation`はアクターの新しい化身を指します。`me`はこのメッセージの配信時にスケジュールされ、`reincarnation`はそうではありません。

`OnBecome`を処理中にスローされた例外は、発信元の`become`呼び出しに伝播します。
