```
send_soft_trigger(id::Integer, start::ASI_BOOL)
```

元のドキュメントから: ソフトトリガーを送信します。エッジトリガーの場合、真を設定するだけで、露光を開始するための立ち上がりトリガーを送信することを意味します。レベルトリガーの場合、最初に真を設定する必要があり、これは露光を開始することを意味し、偽を設定することは露光を停止することを意味します。CameraInfoのIsTriggerCamが真のときにのみ呼び出す必要があります。
