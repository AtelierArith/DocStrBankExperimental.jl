```
gif_ellipse(P, lat1 = deg2rad(45);
            dt                   = 0.1,
            di::Int              = 10,
            speedup::Int         = 60,
            conf_units::Symbol   = :m,
            μ                    = zeros(eltype(P),2),
            conf                 = 0.95,
            clip                 = Inf,
            n::Int               = 61,
            lim                  = 500,
            margin::Int          = 2,
            axis::Bool           = true,
            plot_eigax::Bool     = false,
            bg_color::Symbol     = :white,
            ce_color::Symbol     = :black,
            b_e::AbstractBackend = gr(),
            save_plot::Bool      = false,
            ellipse_gif::String  = "conf_ellipse.gif")
```

`2` x `2` (x `N`) 共分散行列の (位置) 信頼楕円の GIF アニメーションを作成します。

**引数:**

  * `P`:           `2` x `2` (x `N`) 共分散行列
  * `lat1`:        (オプション) 名目緯度 [rad]、`conf_units = :m` または `:ft` の場合のみ使用
  * `dt`:          (オプション) 測定時間ステップ [s]
  * `di`:          (オプション) GIF 測定間隔 (例: `di = 10` は 10 番目の測定を使用)
  * `speedup`:     (オプション) GIF のスピードアップ (例: `speedup = 60` は 60 倍速)
  * `conf_units`:  (オプション) 信頼楕円の単位 {`:m`,`:ft`,`:deg`,`:rad`}
  * `μ`:           (オプション) 信頼楕円の中心 [`conf_units`]
  * `conf`:        (オプション) パーセンタイル {0:1}
  * `clip`:        (オプション) クリッピング半径 [`conf_units`]
  * `n`:           (オプション) 信頼楕円の点の数
  * `lim`:         (オプション) プロットの `x` & `y` 制限 (`-lim`,`lim`) [`conf_units`]
  * `margin`:      (オプション) プロット周囲のマージン [mm]
  * `axis`:        (オプション) true の場合、軸を表示
  * `plot_eigax`:  (オプション) true の場合、主軸と副軸を表示
  * `bg_color`:    (オプション) 背景色
  * `ce_color`:    (オプション) 信頼楕円の色
  * `b_e`:         (オプション) プロットバックエンド
  * `save_plot`:   (オプション) true の場合、`g1` を `ellipse_gif` として保存
  * `ellipse_gif`: (オプション) 保存する信頼楕円 GIF ファイルのパス/名前 (`.gif` 拡張子はオプション)

**戻り値:**

  * `g1`: 信頼楕円 GIF アニメーション
