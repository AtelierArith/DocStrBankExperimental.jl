```
PressureSpectrumAmplitude(hc, dt, t0=zero(dt), istonal::Bool=false)
```

離散フーリエ変換の半複素形式 `hc`、時間ステップサイズ `dt`、および初期時間 `t0` から圧力振幅の狭帯域スペクトルを構築します。`istonal` の `Bool` 引数が `true` の場合、圧力スペクトルはトーナルであり、したがって離散周波数に集中しています。`false` の場合、スペクトルは各周波数帯域で一定であると仮定されます。
