等値面を描画します。

この関数は、ファイルを読み込むか、二次元配列と現在のカラーマップを使用して画像を描画できます。等値より大きい値は等値面の外側として表示され、等値より小さい値は等値面の内側として表示されます。

:param v: ボリュームデータ :param isovalue: 等値

**使用例:**

.. code-block:: julia

```
julia> # 例データを作成
julia> s = LinRange(-1, 1, 40)
julia> v = 1 .- (s .^ 2 .+ (s .^ 2)' .+ reshape(s,1,1,:) .^ 2) .^ 0.5
julia> # 2d配列から画像を描画
julia> isosurface(v, isovalue=0.2)
```
