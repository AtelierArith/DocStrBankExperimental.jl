```
target!(ts::TestState)
```

もし `ts` に向かうべきターゲットが設定されている場合、これは `ts` がもう生成しないようになるまで選択シーケンスを調整して、そのターゲットに向かって登ろうとします。

もし `ts` が現在遭遇したエラーを追跡している場合、そこにおけるスタックトレースを最小化しようとします。
