画像を描画します。

この関数は、ファイルを読み込むか、二次元配列と現在のカラーマップを使用して画像を描画できます。

:param image: 画像ファイル名または二次元配列

**使用例:**

.. code-block:: julia

```
julia> # 例のデータを作成
julia> x = LinRange(-2, 2, 40)
julia> y = LinRange(0, pi, 20)
julia> z = sin.(x') .+ cos.(y)
julia> # 2d配列から画像を描画
julia> imshow(z)
julia> # ファイルから画像を描画
julia> imshow("example.png")
```
