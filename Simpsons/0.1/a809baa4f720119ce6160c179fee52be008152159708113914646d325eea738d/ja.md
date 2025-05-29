```
has_simpsons_paradox(df, cause, effect, factor;
    continuous_threshold = 5, cmax = 5, verbose = true)
```

因子によって集約されたデータがシンプソンの逆説を示す場合はtrueを返します。`cause`および`effect`列は、すでに数値型でない場合はInt列に変換されます。連続データの`factor`列（`continuous_threshold`以上の離散レベルを持つもの）は、あまり多くのクラスタを避けるために、最大cmaxクラスタにグループ化されます。verboseがtrueの場合、全体のデータとグループの回帰傾斜の方向を印刷します。例:     df = DataFrame(         treatment = [1, 2, 1, 1, 2, 2],         recovery = [1, 0, 1, 1, 0, 0],         kidney*stone*size = ["small", "small", "large", "small", "large", "large"])     has*simpsons*paradox(df, :treatment, :recovery, :kidney*stone*size) ```
