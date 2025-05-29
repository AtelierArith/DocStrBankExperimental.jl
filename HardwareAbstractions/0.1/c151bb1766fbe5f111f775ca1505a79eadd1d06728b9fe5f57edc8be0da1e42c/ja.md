```
y,u,r = run_control_2DOF(process, sysFB[, sysFF]; duration = 10, reference(t) = sign(sin(2π*t)))
```

フィードバックおよびフィードフォワードコントローラがそれぞれ `sysFB` と `sysFF` で与えられるプロセスに対して制御実験を行います。両方とも `StateSpace` 型です。

`reference` はスカラー `t`（秒単位の時間）を受け取り、スカラー `r` を出力する参照生成関数で、デフォルトは `reference(t) = sign(sin(2π*t))` です。

出力 `y,u,r` はそれぞれビーム角度、制御信号、参照を表します。 ![block diagram](feedback4.png)
