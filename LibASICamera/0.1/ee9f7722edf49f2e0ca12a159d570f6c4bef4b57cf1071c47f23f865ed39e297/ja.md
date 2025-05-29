```
set_trigger_output_config(id::Integer, pin::ASI_TRIG_OUTPUT_PIN, high::ASI_BOOL, delay, duration)
```

トリガーポートの出力ピン（AまたはB）を設定します。duration <= 0 の場合、この出力ピンは閉じられます。CameraInfo の IsTriggerCam が true のときのみ呼び出す必要があります。

# 引数:

```
id: カメラID
pin: 出力用のピンを選択
high: true の場合、選択したピンは有効なときに信号として高レベルを出力します。
delay: カメラがトリガ信号を受信してから有効レベルを出力するまでの遅延。0 μs - 2,000,000,000 μs の範囲。
duration: 有効レベル出力の持続時間。遅延と同じ範囲。
```
