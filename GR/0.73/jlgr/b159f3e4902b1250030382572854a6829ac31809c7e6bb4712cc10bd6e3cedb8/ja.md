1つ以上のステップまたは階段プロットを描画します。

この関数は、次のいずれかを受け取ることができます：

  * x 値と y 値、または
  * x 値と y 値を決定するための呼び出し可能オブジェクト、または
  * y 値のみ、インデックスを x 値として使用

:param args: プロットするデータ :param where: pre, mid または post、2つの y 値の間のステップをどこに配置するかを決定します

**使用例：**

.. code-block:: julia     julia> # サンプルデータを作成     julia> x = LinRange(-2, 2, 40)     julia> y = 2 .* x .+ 4     julia> # x と y をプロット     julia> stairs(x, y)     julia> # x と呼び出し可能オブジェクトをプロット     julia> stairs(x, x -> x^3 + x^2 + x)     julia> # y をプロットし、そのインデックスを x 値として使用     julia> stairs(y)     julia> # 各位置の x の直後に次の y ステップを使用     julia> stairs(y, where="pre")     julia> # 2つの x 位置の間に次の y ステップを使用     julia> stairs(y, where="mid")     julia> # 次の x 位置の直前に次の y ステップを使用     julia> stairs(y, where="post")
