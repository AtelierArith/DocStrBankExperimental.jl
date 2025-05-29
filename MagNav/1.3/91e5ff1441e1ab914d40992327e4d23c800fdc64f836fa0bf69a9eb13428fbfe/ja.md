```
create_P0(lat1 = deg2rad(45);
          init_pos_sigma   = 3.0,
          init_alt_sigma   = 0.001,
          init_vel_sigma   = 0.01,
          init_att_sigma   = deg2rad(0.01),
          ha_sigma         = 0.001,
          a_hat_sigma      = 0.01,
          acc_sigma        = 0.000245,
          gyro_sigma       = 0.00000000727,
          fogm_sigma       = 3.0,
          vec_sigma        = 1000.0,
          vec_states::Bool = false,
          fogm_state::Bool = true,
          P0_TL            = [])
```

初期共分散行列 `P0` を作成します。

**引数:**

  * `lat1`:           初期の近似緯度 [rad]
  * `init_pos_sigma`: (オプション) 初期位置の不確実性 [m]
  * `init_alt_sigma`: (オプション) 初期高度の不確実性 [m]
  * `init_vel_sigma`: (オプション) 初期速度の不確実性 [m/s]
  * `init_att_sigma`: (オプション) 初期姿勢の不確実性 [rad]
  * `ha_sigma`:       (オプション) 気圧計補助の高度バイアス [m]
  * `a_hat_sigma`:    (オプション) 気圧計補助の垂直加速度バイアス [m/s^2]
  * `acc_sigma`:      (オプション) 加速度計のバイアス [m/s^2]
  * `gyro_sigma`:     (オプション) ジャイロスコープのバイアス [rad/s]
  * `fogm_sigma`:     (オプション) FOGMの全体バイアス [nT]
  * `vec_sigma`:      (オプション) ベクトル磁力計のノイズ標準偏差
  * `vec_states`:     (オプション) trueの場合、ベクトル磁力計の状態を含める
  * `fogm_state`:     (オプション) trueの場合、FOGMの全体バイアス状態を含める
  * `P0_TL`:          (オプション) 初期のトレス・ローソン共分散行列

**戻り値:**

  * `P0`: 初期共分散行列
