別のプロットの上に1つ以上の線グラフを描画します。

この関数は、次のいずれかを受け取ることができます：

  * x 値と y 値、または
  * x 値と y 値を決定するための呼び出し可能なオブジェクト、または
  * y 値のみ、インデックスを x 値として使用

:param args: プロットするデータ

**使用例：**

.. code-block:: julia

```
julia> # サンプルデータを作成
julia> x = LinRange(-2, 2, 40)
julia> y = 2 .* x .+ 4
julia> # 最初のプロットを描画
julia> plot(x, y)
julia> # その上にグラフをプロット
julia> oplot(x, x -> x^3 + x^2 + x)
```
