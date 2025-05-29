三次元散布図を1つ以上描画します。

x、y、zの値に加えて、マーカーの色の値を提供することができます。色の値は、現在のカラーマップと組み合わせて使用されます。

:param x: プロットするx座標 :param y: プロットするy座標 :param z: プロットするz座標 :param c: プロットするオプションの色の値

**使用例:**

.. code-block:: julia

```
julia> # サンプルデータを作成
julia> x = 2 .* rand(100) .- 1
julia> y = 2 .* rand(100) .- 1
julia> z = 2 .* rand(100) .- 1
julia> c = 999 .* rand(100) .+ 1
julia> # 点をプロット
julia> scatter3(x, y, z)
julia> # 色付きで点をプロット
julia> scatter3(x, y, z, c)
```
