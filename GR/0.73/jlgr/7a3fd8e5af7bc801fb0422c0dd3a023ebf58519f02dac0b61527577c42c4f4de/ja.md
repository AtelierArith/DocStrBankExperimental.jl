三次元の線プロットを1つ以上描画します。

:param x: プロットするx座標 :param y: プロットするy座標 :param z: プロットするz座標

**使用例:**

.. code-block:: julia

```
julia> # 例のデータを作成
julia> x = LinRange(0, 30, 1000)
julia> y = cos.(x) .* x
julia> z = sin.(x) .* x
julia> # 点をプロット
julia> plot3(x, y, z)
```
