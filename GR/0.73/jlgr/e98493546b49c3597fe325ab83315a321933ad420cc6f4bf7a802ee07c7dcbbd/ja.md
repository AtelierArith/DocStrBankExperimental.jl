1つ以上の線グラフを描画します。

この関数は、以下の1つまたは複数を受け取ることができます：

  * x 値と y 値、または
  * x 値と y 値を決定するための呼び出し可能な関数、または
  * y 値のみ、インデックスを x 値として使用

:param args: プロットするデータ

**使用例:**

.. code-block:: julia-repl

```
julia> # 例のデータを作成
julia> x = LinRange(-2, 2, 40)
julia> y = 2 .* x .+ 4
julia> # x と y をプロット
julia> plot(x, y)
julia> # x と呼び出し可能な関数をプロット
julia> plot(x, t -> t^3 + t^2 + t)
julia> # y をプロットし、x 値としてそのインデックスを使用
julia> plot(y)
```
