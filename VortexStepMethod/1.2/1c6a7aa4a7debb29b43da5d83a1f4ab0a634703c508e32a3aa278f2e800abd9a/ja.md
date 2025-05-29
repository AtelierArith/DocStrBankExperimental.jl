```
RamAirWing(obj_path, dat_path; kwargs...)
```

3Dジオメトリとエアフォイルデータファイルからラムエアウィングモデルを作成します。

このコンストラクタは、次の手順で完全な空力モデルを構築します。

1. .objファイルからウィングジオメトリを読み込むまたは生成する
2. エアフォイル.datファイルから空力ポーラを作成する
3. 慣性特性と座標変換を計算する
4. 制御面とパネル分布を設定する

# 引数

  * `obj_path`: 3Dウィングジオメトリを含む.objファイルへのパス
  * `dat_path`: 2Dエアフォイルプロファイルを含む.datファイルへのパス

# キーワード引数

  * `crease_frac=0.9`: 正規化されたトレーリングエッジヒンジ位置 (0-1)
  * `wind_vel=10.0`: XFoil分析のための基準風速 (m/s)
  * `mass=1.0`: ウィングの質量 (kg)
  * `n_panels=56`: 翼幅にわたる空力パネルの数
  * `n_groups=4`: 変形のための制御グループの数
  * `n_sections=n_panels+1`: スパン方向の断面の数
  * `align_to_principal=false`: ボディフレームを慣性の主軸に整列させる
  * `spanwise_distribution=UNCHANGED`: パネル分布のタイプ
  * `remove_nan=true`: 空力データ内のNaN値を補間する
  * `alpha_range=deg2rad.(-5:1:20)`: ポーラの迎角範囲 (rad)
  * `delta_range=deg2rad.(-5:1:20)`: ポーラのトレーリングエッジ偏向範囲 (rad)
  * prn=true: 情報メッセージを印刷するかどうか

# 戻り値

空力シミュレーションの準備が整った完全に初期化された`RamAirWing`インスタンス。

# 例

```julia
# ジオメトリファイルからラムエアウィングを作成
wing = RamAirWing(
    "path/to/wing.obj",
    "path/to/airfoil.dat";
    mass=1.5,
    n_panels=40,
    n_groups=4
)
```
