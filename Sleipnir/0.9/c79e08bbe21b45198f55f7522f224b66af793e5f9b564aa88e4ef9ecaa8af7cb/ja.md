```
downscale_2D_climate(climate_step::Dict, glacier::Glacier2D) -> Climate2Dstep
```

気候データを提供された氷河情報に基づいて2Dグリッドにダウンサイジングします。

# 引数

  * `climate_step::Dict`: 特定の時間ステップの気候データを含む辞書。期待されるキーは次のとおりです：

      * `"avg_temp"`: 平均気温。
      * `"temp"`: 気温。
      * `"prcp"`: 降水量。
      * `"gradient"`: 気温勾配。
      * `"avg_gradient"`: 平均気温勾配。
      * `"ref_hgt"`: 参照高さ。
  * `glacier::Glacier2D`: 氷河データを含む`Glacier2D`オブジェクト。期待されるフィールドは次のとおりです：

      * `S`: 表面標高データ。
      * `Coords`: 経度と緯度の座標用のキー`"lon"`と`"lat"`を持つ辞書。

# 戻り値

  * `Climate2Dstep`: ダウンサイジングされた気候データを含む`Climate2Dstep`オブジェクトで、フィールドは次のとおりです：

      * `temp`: 気温の2D配列。
      * `PDD`: 正の度日数の2D配列。
      * `snow`: 雪の降水量の2D配列。
      * `rain`: 雨の降水量の2D配列。
      * `gradient`: 気温勾配。
      * `avg_gradient`: 平均気温勾配。
      * `x`: 経度座標。
      * `y`: 緯度座標。
      * `ref_hgt`: 参照高さ。

# 説明

この関数は氷河の表面標高データに基づいてダミーの2D配列を作成し、これらの配列に気候ステップデータを適用します。次に、ダウンサイジングされた気候データを持つ`Climate2Dstep`オブジェクトを構築し、選択された期間の雪/雨の割合を計算するために気温勾配を適用します。
