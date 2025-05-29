```
create_ins(traj::Traj;
           init_pos_sigma = 3.0,
           init_alt_sigma = 0.001,
           init_vel_sigma = 0.01,
           init_att_sigma = deg2rad(0.01),
           VRW_sigma      = 0.000238,
           ARW_sigma      = 0.000000581,
           baro_sigma     = 1.0,
           ha_sigma       = 0.001,
           a_hat_sigma    = 0.01,
           acc_sigma      = 0.000245,
           gyro_sigma     = 0.00000000727,
           baro_tau       = 3600.0,
           acc_tau        = 3600.0,
           gyro_tau       = 3600.0,
           save_h5::Bool  = false,
           ins_h5::String = "ins_data.h5")
```

真の軌道に関するINS軌道を作成します。17状態のPinson誤差モデルを伝播させてINS誤差を生成します。

**引数:**

  * `traj`:           `Traj` 軌道構造体
  * `init_pos_sigma`: (オプション) 初期位置の不確実性 [m]
  * `init_alt_sigma`: (オプション) 初期高度の不確実性 [m]
  * `init_vel_sigma`: (オプション) 初期速度の不確実性 [m/s]
  * `init_att_sigma`: (オプション) 初期姿勢の不確実性 [rad]
  * `VRW_sigma`:      (オプション) 速度ランダムウォーク [m/s^2 /sqrt(Hz)]
  * `ARW_sigma`:      (オプション) 角度ランダムウォーク [rad/s /sqrt(Hz)]
  * `baro_sigma`:     (オプション) バロメーターのバイアス [m]
  * `ha_sigma`:       (オプション) バロメーター支援高度バイアス [m]
  * `a_hat_sigma`:    (オプション) バロメーター支援垂直加速度バイアス [m/s^2]
  * `acc_sigma`:      (オプション) 加速度計のバイアス [m/s^2]
  * `gyro_sigma`:     (オプション) ジャイロスコープのバイアス [rad/s]
  * `baro_tau`:       (オプション) バロメーターの時定数 [s]
  * `acc_tau`:        (オプション) 加速度計の時定数 [s]
  * `gyro_tau`:       (オプション) ジャイロスコープの時定数 [s]
  * `save_h5`:        (オプション) trueの場合、`ins`を`ins_h5`に保存
  * `ins_h5`:         (オプション) 保存するINSデータHDF5ファイルのパス/名前（`.h5`拡張子はオプション）

**戻り値:**

  * `ins`: `INS` 慣性航法システム構造体
