```
create_informed_xyz(xyz::XYZ, ind, mapS::Union{MapS,MapSd,MapS3D},
                    use_mag::Symbol, use_vec::Symbol, TL_coef::Vector;
                    terms::Vector{Symbol} = [:permanent,:induced,:eddy],
                    disp_min = 100,
                    disp_max = 500,
                    Bt_disp  = 50,
                    Bt_scale = 50000)
```

既存のデータから知識に基づいたデータを作成します。マップ情報、磁力計の読み取りを含む`XYZ`構造、およびフィッティングされたトレス-ローソンモデルが与えられた場合、この関数は、全体の飛行が（`disp_min`,`disp_max`）によって横にシフトされていた場合に`use_mag`と`mag_1_c`が収集したであろう一貫した、シフトされた`XYZ`構造を作成します。これは、代替マップ位置による期待される変化と、補完された航空機フィールドによる変化を更新するためにマップ情報のテイラー展開を利用します。航空機の「ノイズ」は、新しい`XYZ`データの`use_mag`に引き継がれます。

**引数:**

  * `xyz`:      `XYZ`飛行データ構造
  * `ind`:      選択されたデータインデックス
  * `mapS`:     `MapS`、`MapSd`、または`MapS3D`スカラー磁気異常マップ構造
  * `use_mag`:  `y`ターゲットベクトルに使用する補正されていないスカラー磁力計 {`:mag_1_uc` など}
  * `use_vec`:  トレス-ローソン`A`行列に使用するベクトル磁力計（フラックスゲート） {`:flux_a` など}
  * `TL_coef`:  トレス-ローソン係数
  * `terms`:    （オプション）使用するトレス-ローソン項 {`:permanent`,`:induced`,`:eddy`}
  * `disp_min`: （オプション）最小軌道変位 [m]
  * `disp_max`: （オプション）最大軌道変位 [m]
  * `Bt_disp`:  （オプション）目標総磁場の大きさの変位オフセット [nT]
  * `Bt_scale`: （オプション）誘導および渦電流項のスケーリング係数 [nT]

**戻り値:**

  * `xyz_disp`: シフトされた軌道と修正された磁力計の読み取りを持つ`XYZ`飛行データ構造
