```
plot_shapley(df_shap, baseline_shap,
             range_shap::UnitRange = UnitRange(axes(df_shap,1));
             title::String         = "features $range_shap",
             dpi::Int              = 200)
```

特徴の重要性（シャプレー効果）の水平棒グラフをプロットします。

**引数:**

  * `df_shap`:       シャプレー効果のデータフレーム

| **フィールド**      | **型**    | **説明**    |
|:-------------- |:-------- |:--------- |
| `feature_name` | `Symbol` | 特徴名       |
| `mean_effect`  | `Real`   | 平均シャプレー効果 |

  * `baseline_shap`: シャプレー効果の切片
  * `range_shap`:    （オプション）プロットするシャプレー効果の範囲（長さを約20に制限）
  * `dpi`:           （オプション）ドット毎インチ（画像解像度）
  * `title`:         （オプション）プロットタイトル

**戻り値:**

  * `p1`: シャプレー効果のプロット
