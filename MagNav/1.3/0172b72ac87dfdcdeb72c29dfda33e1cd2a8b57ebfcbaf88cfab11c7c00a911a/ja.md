```
create_model(dt = 0.1, lat1 = deg2rad(45);
             init_pos_sigma   = 3.0,
             init_alt_sigma   = 0.001,
             init_vel_sigma   = 0.01,
             init_att_sigma   = deg2rad(0.01),
             meas_var         = 3.0^2,
             VRW_sigma        = 0.000238,
             ARW_sigma        = 0.000000581,
             baro_sigma       = 1.0,
             ha_sigma         = 0.001,
             a_hat_sigma      = 0.01,
             acc_sigma        = 0.000245,
             gyro_sigma       = 0.00000000727,
             fogm_sigma       = 3.0,
             vec_sigma        = 1000.0,
             TL_sigma         = [],
             baro_tau         = 3600.0,
             acc_tau          = 3600.0,
             gyro_tau         = 3600.0,
             fogm_tau         = 600.0,
             vec_states::Bool = false,
             fogm_state::Bool = true,
             P0_TL            = [])
```

EKFまたはMPFで使用するための磁気ナビゲーションフィルタモデルを作成します。

**引数:**

  * `dt`:             測定時間ステップ [s]
  * `lat1`:           初期の近似緯度 [rad]
  * `init_pos_sigma`: (オプション) 初期位置の不確実性 [m]
  * `init_alt_sigma`: (オプション) 初期高度の不確実性 [m]
  * `init_vel_sigma`: (オプション) 初期速度の不確実性 [m/s]
  * `init_att_sigma`: (オプション) 初期姿勢の不確実性 [rad]
  * `meas_var`:       (オプション) 測定（ホワイト）ノイズの分散 [nT^2]
  * `VRW_sigma`:      (オプション) 速度ランダムウォーク [m/s^2 /sqrt(Hz)]
  * `ARW_sigma`:      (オプション) 角度ランダムウォーク [rad/s /sqrt(Hz)]
  * `baro_sigma`:     (オプション) バロメーターのバイアス [m]
  * `ha_sigma`:       (オプション) バロメーター補助の高度バイアス [m]
  * `a_hat_sigma`:    (オプション) バロメーター補助の垂直加速度バイアス [m/s^2]
  * `acc_sigma`:      (オプション) 加速度計のバイアス [m/s^2]
  * `gyro_sigma`:     (オプション) ジャイロスコープのバイアス [rad/s]
  * `fogm_sigma`:     (オプション) FOGMの全体的なバイアス [nT]
  * `vec_sigma`:      (オプション) ベクトル磁気計のノイズ標準偏差
  * `TL_sigma`:       (オプション) トレス・ローソン係数の推定標準偏差
  * `baro_tau`:       (オプション) バロメーターの時定数 [s]
  * `acc_tau`:        (オプション) 加速度計の時定数 [s]
  * `gyro_tau`:       (オプション) ジャイロスコープの時定数 [s]
  * `fogm_tau`:       (オプション) FOGMの全体的な時定数 [s]
  * `vec_states`:     (オプション) trueの場合、ベクトル磁気計の状態を含める
  * `fogm_state`:     (オプション) trueの場合、FOGMの全体的なバイアス状態を含める
  * `P0_TL`:          (オプション) 初期トレス・ローソン共分散行列

**戻り値:**

  * `P0`: 初期共分散行列
  * `Qd`: 離散時間プロセス/システムノイズ行列
  * `R`:  測定（ホワイト）ノイズの分散
