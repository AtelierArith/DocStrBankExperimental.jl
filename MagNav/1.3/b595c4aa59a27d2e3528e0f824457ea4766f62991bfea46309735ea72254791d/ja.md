```
get_ins(xyz::XYZ, ind = trues(xyz.traj.N);
        N_zero_ll::Int  = 0,
        t_zero_ll::Real = 0,
        err::Real       = 0.0)
```

特定のインデックスで慣性航法システムデータを取得します。ゼロにすることも可能です。

**引数:**

  * `xyz`:       `XYZ` フライトデータ構造体
  * `ind`:       （オプション）選択されたデータインデックス
  * `N_zero_ll`: （オプション）真実（`xyz.traj`）に対してINSの緯度/経度をゼロにするサンプル数（インスタンス）
  * `t_zero_ll`: （オプション）真実（`xyz.traj`）に対してINSの緯度/経度をゼロにする時間の長さ、`N_zero_ll`を上書きします
  * `err`:       （オプション）追加の位置誤差 [m]

**戻り値:**

  * `ins`: `ind`での慣性航法システム構造体 `INS`
