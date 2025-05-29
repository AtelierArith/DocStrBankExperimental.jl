```
preview_data(
            xs::Array,
            ys::Array;
            title = randstring(10),
            figsize::Tuple{Number,Number} = (4,3),
            xlab::String = "X label",
            ylab::String = "Y label",
            marker::String = "",
            linestyle::String = "-",
            label_fontsize::Int = 12
)
```

データのプレビュー、次の条件を満たす

  * `xs` xの配列
  * `ys` yの配列
  * `title` 軸のタイトル
  * `figsize` キャンバスのサイズ
  * `xlab` X軸のラベル
  * `ylab` Y軸のラベル
  * `marker` マーカーのスタイル
  * `linestyle` 線のスタイル
  * `label_fontsize` XおよびY軸のラベルのフォントサイズ
