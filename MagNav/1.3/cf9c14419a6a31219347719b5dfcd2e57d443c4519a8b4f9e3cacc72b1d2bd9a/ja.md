```
crlb(traj::Traj, itp_mapS;
     P0         = create_P0(),
     Qd         = create_Qd(),
     R          = 1.0,
     baro_tau   = 3600.0,
     acc_tau    = 3600.0,
     gyro_tau   = 3600.0,
     fogm_tau   = 600.0,
     date       = get_years(2020,185),
     core::Bool = false)
```

クラメール–ラオ下限（CRLB）は、古典的カルマンフィルタを用いて計算されます。方程式は真の軌道に関して評価されます。

**引数:**

  * `traj`:     `Traj` 軌道構造体
  * `itp_mapS`: スカラー地図補間関数 (`f(lat,lon)` または `f(lat,lon,alt)`)
  * `P0`:       （オプション）初期共分散行列
  * `Qd`:       （オプション）離散時間プロセス/システムノイズ行列
  * `R`:        （オプション）測定（ホワイト）ノイズ分散
  * `baro_tau`: （オプション）気圧計の時間定数 [s]
  * `acc_tau`:  （オプション）加速度計の時間定数 [s]
  * `gyro_tau`: （オプション）ジャイロスコープの時間定数 [s]
  * `fogm_tau`: （オプション）FOGMの全般的な時間定数 [s]
  * `date`:     （オプション）IGRFの測定日（小数年） [年]
  * `core`:     （オプション）trueの場合、測定にコア磁場を含める

**戻り値:**

  * `P`: 非線形共分散行列
