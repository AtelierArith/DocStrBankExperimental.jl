```
create_traj(mapS::Union{MapS,MapSd,MapS3D} = get_map(namad);
            alt             = 1000,
            dt              = 0.1,
            t               = 300,
            v               = 68,
            ll1::Tuple      = (),
            ll2::Tuple      = (),
            N_waves::Int    = 1,
            attempts::Int   = 10,
            save_h5::Bool   = false,
            traj_h5::String = "traj_data.h5")
```

`Traj` 軌道構造体を作成し、一定の高度で直線または正弦波の飛行経路を持ちます（2D飛行）。

**引数:**

  * `mapS`:     （オプション）`MapS`、`MapSd`、または `MapS3D` スカラー磁気異常マップ構造体
  * `alt`:      （オプション）高度 [m]
  * `dt`:       （オプション）測定時間ステップ [s]
  * `t`:        （オプション）総飛行時間、`ll2` が設定されている場合は無視されます [s]
  * `v`:        （オプション）おおよその航空機の速度 [m/s]
  * `ll1`:      （オプション）初期 (lat,lon) 点 [deg]
  * `ll2`:      （オプション）最終 (lat,lon) 点 [deg]
  * `N_waves`:  （オプション）経路に沿った正弦波の数
  * `attempts`: （オプション）`mapS` 上で飛行経路を作成する最大試行回数
  * `save_h5`:  （オプション）true の場合、`traj` を `traj_h5` に保存
  * `traj_h5`:  （オプション）軌道データ HDF5 ファイルを保存するパス/名前（`.h5` 拡張子はオプション）

**戻り値:**

  * `traj`: `Traj` 軌道構造体
