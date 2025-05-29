茎プロットを描画します。

この関数は、次のいずれかを受け取ることができます：

  * x 値と y 値、または
  * x 値と y 値を決定するための呼び出し可能なオブジェクト、または
  * y 値のみ、x 値としてそのインデックスを使用

:param args: プロットするデータ

**使用例：**

.. code-block:: julia

```
julia> # 例のデータを作成
julia> x = LinRange(-2, 2, 40)
julia> y = 0.2 .* x .+ 0.4
julia> # x と y をプロット
julia> stem(x, y)
julia> # x と呼び出し可能なオブジェクトをプロット
julia> stem(x, x -> x^3 + x^2 + x + 6)
julia> # y をプロットし、x 値としてそのインデックスを使用
julia> stem(y)
```
