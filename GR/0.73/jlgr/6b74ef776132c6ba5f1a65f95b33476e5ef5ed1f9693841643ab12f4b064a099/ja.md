散布図を1つ以上描画します。

この関数は、以下の1つまたは複数を受け取ることができます：

  * x 値と y 値、または
  * x 値と y 値を決定するための呼び出し可能なオブジェクト、または
  * y 値のみ、インデックスを x 値として使用

x および y 値に加えて、マーカーのサイズと色の値を提供することができます。サイズの値は、通常のサイズのパーセントでマーカーのサイズを決定し、色の値は現在のカラーマップと組み合わせて使用されます。

:param args: プロットするデータ

**使用例：**

.. code-block:: julia

```
julia> # 例のデータを作成
julia> x = LinRange(-2, 2, 40)
julia> y = 0.2 .* x .+ 0.4
julia> # x と y をプロット
julia> scatter(x, y)
julia> # x と呼び出し可能なオブジェクトをプロット
julia> scatter(x, x -> 0.2 * x + 0.4)
julia> # y をプロットし、そのインデックスを x 値として使用
julia> scatter(y)
julia> # サイズと色が増加する対角線をプロット
julia> x = LinRange(0, 1, 11)
julia> y = LinRange(0, 1, 11)
julia> s = LinRange(50, 400, 11)
julia> c = LinRange(0, 255, 11)
julia> scatter(x, y, s, c)
```
