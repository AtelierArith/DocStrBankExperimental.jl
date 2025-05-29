```
create_XYZ0(mapS::Union{MapS,MapSd,MapS3D} = get_map(namad);
            alt            = 1000,
            dt             = 0.1,
            t              = 300,
            v              = 68,
            ll1::Tuple     = (),
            ll2::Tuple     = (),
            N_waves::Int   = 1,
            attempts::Int  = 10,
            info::String   = "Simulated data",
            flight         = 1,
            line           = 1,
            year           = 2023,
            doy            = 154,
            mapV::MapV     = get_map(emm720),
            cor_sigma      = 1.0,
            cor_tau        = 600.0,
            cor_var        = 1.0^2,
            cor_drift      = 0.001,
            cor_perm_mag   = 5.0,
            cor_ind_mag    = 5.0,
            cor_eddy_mag   = 0.5,
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
            fogm_sigma     = 1.0,
            baro_tau       = 3600.0,
            acc_tau        = 3600.0,
            gyro_tau       = 3600.0,
            fogm_tau       = 600.0,
            save_h5::Bool  = false,
            xyz_h5::String = "xyz_data.h5",
            silent::Bool   = false)
```

基本的なフライトデータを作成します。一定の高度（2Dフライト）を仮定しています。必要な引数はありませんが、カスタムデータを作成するために多くの引数が利用可能です。

**軌道引数:**

  * `mapS`:     （オプション）`MapS`、`MapSd`、または`MapS3D`スカラー磁気異常マップ構造体
  * `alt`:      （オプション）高度 [m]
  * `dt`:       （オプション）測定時間ステップ [s]
  * `t`:        （オプション）総フライト時間、`ll2`が設定されている場合は無視されます [s]
  * `v`:        （オプション）おおよその航空機の速度 [m/s]
  * `ll1`:      （オプション）初期（緯度、経度）ポイント [deg]
  * `ll2`:      （オプション）最終（緯度、経度）ポイント [deg]
  * `N_waves`:  （オプション）経路に沿ったサイン波の数
  * `attempts`: （オプション）`mapS`上でフライトパスを作成する最大試行回数
  * `info`:     （オプション）フライトデータ情報
  * `flight`:   （オプション）フライト番号
  * `line`:     （オプション）行番号、すなわち`flight`内のセグメント
  * `year`:     （オプション）年
  * `doy`:      （オプション）年の日
  * `mapV`:     （オプション）`MapV`ベクトル磁気異常マップ構造体
  * `save_h5`:  （オプション）trueの場合、`xyz`を`xyz_h5`に保存
  * `xyz_h5`:   （オプション）フライトデータHDF5ファイルの保存パス/名前（`.h5`拡張子はオプション）

**補償された測定腐敗引数:**

  * `cor_var`:        （オプション）腐敗測定（ホワイト）ノイズ分散 [nT^2]
  * `fogm_sigma`:     （オプション）FOGMの全体的なバイアス [nT]
  * `fogm_tau`:       （オプション）FOGMの全体的な時間定数 [s]

**非補償測定腐敗引数:**

  * `cor_sigma`:      （オプション）腐敗FOGMの全体的なバイアス [nT]
  * `cor_tau`:        （オプション）腐敗FOGMの全体的な時間定数 [s]
  * `cor_var`:        （オプション）腐敗測定（ホワイト）ノイズ分散 [nT^2]
  * `cor_drift`:      （オプション）腐敗測定の線形ドリフト [nT/s]
  * `cor_perm_mag`:   （オプション）腐敗永久場TL係数の標準偏差
  * `cor_ind_mag`:    （オプション）腐敗誘導場TL係数の標準偏差
  * `cor_eddy_mag`:   （オプション）腐敗渦電流TL係数の標準偏差

**INS引数:**

  * `init_pos_sigma`: （オプション）初期位置の不確実性 [m]
  * `init_alt_sigma`: （オプション）初期高度の不確実性 [m]
  * `init_vel_sigma`: （オプション）初期速度の不確実性 [m/s]
  * `init_att_sigma`: （オプション）初期姿勢の不確実性 [rad]
  * `VRW_sigma`:      （オプション）速度のランダムウォーク [m/s^2 /sqrt(Hz)]
  * `ARW_sigma`:      （オプション）角度のランダムウォーク [rad/s /sqrt(Hz)]
  * `baro_sigma`:     （オプション）気圧計のバイアス [m]
  * `ha_sigma`:       （オプション）気圧計補助高度のバイアス [m]
  * `a_hat_sigma`:    （オプション）気圧計補助垂直加速度のバイアス [m/s^2]
  * `acc_sigma`:      （オプション）加速度計のバイアス [m/s^2]
  * `gyro_sigma`:     （オプション）ジャイロスコープのバイアス [rad/s]
  * `baro_tau`:       （オプション）気圧計の時間定数 [s]
  * `acc_tau`:        （オプション）加速度計の時間定数 [s]
  * `gyro_tau`:       （オプション）ジャイロスコープの時間定数 [s]

**一般引数:**

  * `silent`: （オプション）trueの場合、出力なし

**戻り値:**

  * `xyz`: `XYZ0`フライトデータ構造体
