```
map_combine(mapS_vec::Vector, mapS_fallback::MapS = get_map(namad);
            map_info::String   = "Combined map",
            N_levels::Int      = 3,
            dx                 = get_step(mapS_vec[1].xx),
            dy                 = get_step(mapS_vec[1].yy),
            xx_lim::Tuple      = get_lim(mapS_vec[1].xx,0.5),
            yy_lim::Tuple      = get_lim(mapS_vec[1].yy,0.5),
            α                  = 200,
            use_fallback::Bool = true)
```

異なる高度で地図を組み合わせます。最も低い地図と最も高い地図は直接使用され（再サンプリングとリサイズを伴う）、中間の地図は `N_levels` によって決定されます。

**引数:**

  * `mapS_vec`:      `MapS` スカラー磁気異常地図構造体のベクター
  * `mapS_fallback`: （オプション）フォールバック `MapS` スカラー磁気異常地図構造体
  * `map_info`:      （オプション）地図情報
  * `N_levels`:      （オプション）地図の高度レベルの数
  * `dx`:            （オプション）希望するx方向の地図ステップサイズ
  * `dy`:            （オプション）希望するy方向の地図ステップサイズ
  * `xx_lim`:        （オプション）長さ-`2` x方向の地図制限 `(xx_min,xx_max)`
  * `yy_lim`:        （オプション）長さ-`2` y方向の地図制限 `(yy_min,yy_max)`
  * `α`:             （オプション）下方継続のための正則化パラメータ
  * `use_fallback`:  （オプション）trueの場合、欠損した地図データに `mapS_fallback` を使用

**戻り値:**

  * `mapS3D`: `MapS3D` 3D（マルチレベル）スカラー磁気異常地図構造体
