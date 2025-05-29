```
set_xylabels!(
            axs::Array,
            xlabels::Union{Array{String,1},String},
            ylabels::Union{Array{String,1},String};
            fontsize::Number = 16
)
```

軸に対してX軸とY軸のラベルを設定します。

  * `axs` 軸の配列
  * `xlabels` X軸のラベル
  * `ylabels` Y軸のラベル
  * `fontsize` オプション: ラベルのフォントサイズ
