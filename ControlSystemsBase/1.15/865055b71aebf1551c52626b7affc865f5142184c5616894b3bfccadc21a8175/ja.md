```
pidplots(P, args...; params_p, params_i, params_d=0, form=:standard, ω=0, grid=false, kwargs...)
```

プロセス `P` の周りに PID コントローラを用いてループを閉じるために関連するプロットを表示します。コントローラは `params` で供給され、以下のいずれかの形式で表示されます：

  * `:standard` - `Kp*(1 + 1/(Ti*s) + Td*s)`
  * `:series` - `Kc*(1 + 1/(τi*s))*(τd*s + 1)`
  * `:parallel` - `Kp + Ki/s + Kd*s`

送信された値は配列であり、複数の異なるコントローラを評価することができます。また、`grid=true` の場合、すべての可能な値の組み合わせに対してグリッドサーチが行われます。

利用可能なプロットは `:gof`（Gang of four）、`:nyquist`、`:controller`（コントローラ TF のボードプロット）、および `:pz`（極-零マップ）であり、関数に追加の引数として供給する必要があります。

また、ボードおよびナイキストプロットで使用される周波数ベクトル `ω` を供給することもできます。

他に `loopshapingPI`、`stabregionPID` も参照してください。
