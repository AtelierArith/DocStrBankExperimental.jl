```
map_combine(mapS::MapS, mapS_fallback::MapS = get_map(namad);
            map_info::String = mapS.info,
            xx_lim::Tuple    = get_lim(mapS.xx,0.1),
            yy_lim::Tuple    = get_lim(mapS.yy,0.1),
            α                = 200)
```

同じ高度で2つの地図を結合します。

**引数:**

  * `mapS`:          `MapS` スカラー磁気異常マップ構造体
  * `mapS_fallback`: (オプション) フォールバック `MapS` スカラー磁気異常マップ構造体
  * `map_info`:      (オプション) マップ情報
  * `xx_lim`:        (オプション) 長さ`2`のx方向マップ制限 `(xx_min,xx_max)`
  * `yy_lim`:        (オプション) 長さ`2`のy方向マップ制限 `(yy_min,yy_max)`
  * `α`:             (オプション) 下方継続のための正則化パラメータ

**戻り値:**

  * `mapS`: `MapS` スカラー磁気異常マップ構造体、結合されたもの
