```
Verbose(s::LearningStrategy)
Verbose(s::LearningStrategy, io::IO)
```

LearningStrategy `s` に出力を印刷することを許可します。

  * `finished(s, args...) == true` のときに自動的に印刷されます。
  * 他のメソッドは印刷を追加するためにオーバーロードする必要があります。

      * 例えば: `update!(model, v::Verbose{MyStrategy}, item) = ...`
