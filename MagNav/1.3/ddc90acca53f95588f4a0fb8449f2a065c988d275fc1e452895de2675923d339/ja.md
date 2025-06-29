```
get_traj(traj_file::String, field::Symbol = :traj;
         dt            = 0.1,
         tt_sort::Bool = true,
         silent::Bool  = false)
```

保存されたCSV、HDF5、またはMATファイルから軌道データを取得します。必要なフィールドは`lat`、`lon`、および`alt`（位置）のみです。

CSVまたはHDF5ファイルが提供される場合、ファイル内の可能な列/フィールドは次のとおりです：

| **フィールド** | **タイプ** | **説明**                                                              |
|:--------- |:------- |:------------------------------------------------------------------- |
| `dt`      | スカラー    | 測定時間ステップ [s]                                                        |
| `tt`      | ベクトル    | 時間 [s]                                                              |
| `lat`     | ベクトル    | 緯度 [deg]                                                            |
| `lon`     | ベクトル    | 経度 [deg]                                                            |
| `alt`     | ベクトル    | 高度 [m]                                                              |
| `vn`      | ベクトル    | 北方向の速度 [m/s]                                                        |
| `ve`      | ベクトル    | 東方向の速度 [m/s]                                                        |
| `vd`      | ベクトル    | 下方向の速度 [m/s]                                                        |
| `fn`      | ベクトル    | 北方向の特定の力 [m/s]                                                      |
| `fe`      | ベクトル    | 東方向の特定の力 [m/s]                                                      |
| `fd`      | ベクトル    | 下方向の特定の力 [m/s]                                                      |
| `Cnb`     | 3x3xN   | 方向余弦行列（ボディからナビゲーション）[-]、CSVファイルには無効（代わりに`roll`、`pitch`、および`yaw`を使用） |
| `roll`    | ベクトル    | ロール [deg]                                                           |
| `pitch`   | ベクトル    | ピッチ [deg]                                                           |
| `yaw`     | ベクトル    | ヨー [deg]                                                            |

MATファイルが提供される場合、上記のフィールドも提供される可能性がありますが、指定された`field` MAT構造体内に含まれている必要があります。これはMATLABコンパニオンがデータを出力する標準的な方法です。

**引数:**

  * `traj_file`: 軌道データCSV、HDF5、またはMATファイルのパス/名前（`.csv`、`.h5`、または`.mat`拡張子が必要）
  * `field`:     （オプション）使用するMATファイル内の構造体フィールド、CSVまたはHDF5ファイルには関連しない
  * `dt`:        （オプション）測定時間ステップ [s]、`traj_file`にない場合のみ使用
  * `silent`:    （オプション）trueの場合、出力なし

**戻り値:**

  * `traj`: `Traj`軌道構造体
