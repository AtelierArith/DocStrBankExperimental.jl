```
set_ylabels!(
            axs::Array,
            ylabels::Array{String,1};
            fontsize::Number = 16
)
set_ylabels!(
            axs::Array,
            ylabels::String;
            fontsize::Number = 16
)
```

軸に対してY軸ラベルを設定します。与えられたもの：

  * `axs` 軸の配列
  * `labels` Y軸ラベル
  * `fontsize` オプション：ラベルのフォントサイズ
