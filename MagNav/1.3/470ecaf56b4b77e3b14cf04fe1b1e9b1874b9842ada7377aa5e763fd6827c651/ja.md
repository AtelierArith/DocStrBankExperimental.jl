```
get_traj(xyz::XYZ, ind = trues(xyz.traj.N))
```

特定のインデックスでの軌道データを取得します。

**引数:**

  * `xyz`: `XYZ` フライトデータ構造体
  * `ind`: （オプション）選択されたデータインデックス

**戻り値:**

  * `traj`: `ind` の軌道構造体 `Traj`
