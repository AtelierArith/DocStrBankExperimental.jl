```
get_igrf(xyz::XYZ, ind = trues(xyz.traj.N);
         frame::Symbol   = :body,
         norm_igrf::Bool = false,
         check_xyz::Bool = true)
```

IGRF地球ベクトルを、軌道情報を含む`XYZ`フライトデータ構造体、妥当なインデックス、IGRF時間（0 CEからの年数）での開始日、および参照フレームを考慮して、ボディまたはナビゲーションフレームで取得します。

**引数:**

  * `xyz`:       `XYZ`フライトデータ構造体
  * `ind`:       （オプション）選択されたデータインデックス
  * `frame`:     （オプション）希望する参照フレーム {`:body`,`:nav`}
  * `norm_igrf`: （オプション）trueの場合、`igrf_vec`を正規化
  * `check_xyz`: （オプション）trueの場合、`xyz`の`igrf`フィールドとクロスチェック

**戻り値:**

  * `igrf_vec`: 長さ`N`のスタックされた`3`つのIGRF座標のベクトルが`frame`内にあります。
