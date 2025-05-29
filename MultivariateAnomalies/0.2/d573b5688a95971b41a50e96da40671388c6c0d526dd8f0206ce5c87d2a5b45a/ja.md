```
mapMovingWindow(function2mw, x, args...; ObsPerYear::Int = 46, windowsize::Int = 9, edgecut::Int = 0, startidx::Int = 1, numoutvars::Int = 0)
mapMovingWindow(function2mw, x; ...)
```

関数（function2mw）を移動ウィンドウ内で適用し、すべての年を含み、時間に沿って実行します。例えば、関数をすべての夏に適用し、その後夏 + 1 タイムステップ ... 結果はそれぞれのウィンドウサイズの中心に書き込まれます。入力軸は時間または時間変数です。出力変数の数は入力変数の数と異なる場合があり、numoutvarsで指定されます。例えば、変数をゼロから一の間の正規化されたランクに変換して異方性を取り除く場合は、次のようになります：     using MultivariateAnomalies     x = randn(10*46, 3)     mapMovingWindow(get*quantile*scores, x, numoutvars = size(x, 2)) ```
