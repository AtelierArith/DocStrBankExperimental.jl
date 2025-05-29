PyPlotは、JuliaがPythonのMatplotlibライブラリ、特にmatplotlib.pyplotモジュールとインターフェースを持つことを可能にし、お気に入りのPythonパッケージを使用してJuliaで美しいプロットを作成できます。

現在文書化されているmatplotlib.pyplot APIのみがエクスポートされています。モジュール内の他の関数を使用するには、matplotlib.pyplot.foo(...)をplt.foo(...)として呼び出すこともできます。たとえば、plt.plot(x, y)も機能します。（また、matplotlibモジュールの生のPyObjectにもPyPlot.matplotlibとしてアクセスできます。）

一般的に、すべての引数はPythonと同じです。

以下は、Juliaでのシンプルなプロットの簡単なデモです：

```
using PyPlot
x = range(0; stop=2*pi, length=1000); y = sin.(3 * x + 4 * cos.(2 * x));
plot(x, y, color="red", linewidth=2.0, linestyle="--")
title("A sinusoidally modulated sinusoid")
```

APIに関する詳細は、matplotlib.pyplotのドキュメントおよびPyPlotのGitHubページを参照してください。
