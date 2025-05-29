```
data, S = record(time::Real = 5; input_device, args=(1,0), chat::Bool=true)
```

`input_device`を使用して`time`秒のオーディオデータを記録します（通常は内蔵マイクにデフォルト設定されています）。

# 入力

  * `time` : 継続時間; デフォルトは5秒

# オプション

  * `input_device::PortAudioDevice = get_default_input_device()` システムのデフォルト
  * `args` : PortAudioStreamへの引数; デフォルトは単一チャネル入力のための`(1,0)`
  * `chat` : 開始/終了メッセージを表示しますか？ デフォルトは`true`

# 出力

  * `data` : 長さ`time * S`のベクター
  * `S` : 入力ストリームの`sample_rate`
