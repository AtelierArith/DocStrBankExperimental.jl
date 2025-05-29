# LaTeXTabulars.jl

![lifecycle](https://img.shields.io/badge/lifecycle-maturing-blue.svg) [![build](https://github.com/tpapp/LaTeXTabulars.jl/workflows/CI/badge.svg)](https://github.com/tpapp/LaTeXTabulars.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/github/tpapp/LaTeXTabulars.jl/graph/badge.svg?token=nscxTtrb6g)](https://codecov.io/github/tpapp/LaTeXTabulars.jl) [![documentation](https://img.shields.io/badge/docs-dev-blue.svg)](https://tpapp.github.io/LaTeXTabulars.jl/dev/)

JuliaからLaTeX形式で表形式のデータを書き出します。

これは*非常に薄いラッパー*であり、基本的にはいくつかのループや繰り返し使用される文字列を避けるためのものです。LaTeXの`tabular`環境がどのように機能するかを知っていること、そして小数点の丸めや整列のような何か特別なことを望む場合は、セルを文字列にフォーマットしていることを前提としています。

このパッケージはマニュアルとドキュメントストリングで文書化されています。
