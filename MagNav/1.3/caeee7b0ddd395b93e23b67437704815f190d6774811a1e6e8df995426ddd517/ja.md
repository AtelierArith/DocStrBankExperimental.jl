```
gif_ellipse(filt_res::FILTres,
            filt_out::FILTout,
            map_map::Map         = mapS_null;
            dt                   = 0.1,
            di::Int              = 10,
            speedup::Int         = 60,
            conf_units::Symbol   = :m,
            μ                    = zeros(eltype(filt_res.P),2),
            conf                 = 0.95,
            clip                 = Inf,
            n::Int               = 61,
            lim                  = 500,
            dpi::Int             = 200,
            margin::Int          = 2,
            axis::Bool           = true,
            plot_eigax::Bool     = false,
            bg_color::Symbol     = :white,
            ce_color::Symbol     = :black,
            map_color::Symbol    = :usgs,
            clims::Tuple         = (),
            b_e::AbstractBackend = gr(),
            save_plot::Bool      = false,
            ellipse_gif::String  = "conf_ellipse.gif")
```

`2` x `2` (x `N`) 共分散行列の位置信頼楕円のGIFアニメーションを作成します。

**引数:**

  * `filt_res`:    `FILTres` フィルタ結果構造体
  * `filt_out`:    `FILTout` フィルタ抽出出力構造体
  * `map_map`:     (オプション) `Map` 磁気異常マップ構造体
  * `dt`:          (オプション) 測定時間ステップ [s]
  * `di`:          (オプション) GIF測定間隔 (例: `di = 10` は10回目の測定を使用)
  * `speedup`:     (オプション) GIFのスピードアップ (例: `speedup = 60` は60倍の速度)
  * `conf_units`:  (オプション) 信頼楕円の単位 {`:m`,`:ft`,`:deg`,`:rad`}
  * `μ`:           (オプション) 信頼楕円の中心 [`conf_units`]
  * `conf`:        (オプション) パーセンタイル {0:1}
  * `clip`:        (オプション) クリッピング半径 [`conf_units`]
  * `n`:           (オプション) 信頼楕円の点の数
  * `lim`:         (オプション) プロットの `x` & `y` 制限 (`-lim`,`lim`) [`conf_units`]
  * `dpi`:         (オプション) インチあたりのドット数 (画像解像度)
  * `margin`:      (オプション) プロット周囲のマージン [mm]
  * `axis`:        (オプション) trueの場合、軸を表示
  * `plot_eigax`:  (オプション) trueの場合、主軸と副軸を表示
  * `bg_color`:    (オプション) 背景色
  * `ce_color`:    (オプション) 信頼楕円の色
  * `map_color`:   (オプション) 塗りつぶし等高線のカラースキーム {`:usgs`,`:gray`,`:gray1`,`:gray2`,`:plasma`,`:magma`}
  * `clims`:       (オプション) 長さ`2`のマップカラーバーの制限 `(cmin,cmax)`
  * `b_e`:         (オプション) プロットバックエンド
  * `save_plot`:   (オプション) trueの場合、`g1`を`ellipse_gif`として保存
  * `ellipse_gif`: (オプション) 保存する信頼楕円GIFファイルのパス/名前 (`.gif`拡張子はオプション)

**戻り値:**

  * `g1`: 信頼楕円GIFアニメーション
