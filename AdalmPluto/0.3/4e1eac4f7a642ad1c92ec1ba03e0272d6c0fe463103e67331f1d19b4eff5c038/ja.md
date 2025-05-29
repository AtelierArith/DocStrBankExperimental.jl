```
updateGainMode!(pluto[, mode])
```

pluto RX チャンネルのゲイン制御モードを変更します。成功しない場合は、エラーコード < 0 を返します。

# 引数

  * `pluto::PlutoSDR` : 変更するラジオ。
  * `mode::GainMode=DEFAULT` : 新しいゲインモード。DEFAULT ≡ FAST_ATTACK。

# 戻り値

  * `errno::Int` : 0 または負のエラーコード。
