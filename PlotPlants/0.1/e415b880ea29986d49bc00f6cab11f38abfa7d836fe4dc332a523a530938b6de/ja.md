```
plot_line_regress!(
            ax::PyObject,
            xs::Array,
            ys::Array;
            linestyle::String = "-",
            intercept::Bool = true,
            interval::Bool = false,
            color::String = "red",
            alpha::Number = 0.3
)
```

軸上に線形回帰と信頼区間をプロットします。与えられた

  * `ax` 与えられた軸
  * `xs` xの配列
  * `ys` yの配列
  * `linestyle` オプション。回帰曲線の線スタイル（デフォルトは "-"）
  * `intercept` オプション：trueの場合、切片を持つデータにフィットします
  * `interval` オプション：trueの場合、フィットしたyの信頼区間をプロットします
  * `color` フィットした曲線の色
  * `alpha` 信頼区間の透明度（曲線と同じ色）
