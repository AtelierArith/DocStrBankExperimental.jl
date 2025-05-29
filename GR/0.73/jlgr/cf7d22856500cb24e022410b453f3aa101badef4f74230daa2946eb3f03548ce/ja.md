1つ以上の極座標プロットを描画します。

この関数は、次のいずれかを受け取ることができます：

  * 角度の値と半径の値、または
  * 角度の値と半径の値を決定するための呼び出し可能な関数

:param args: プロットするデータ

**使用例：**

.. code-block:: julia

```
julia> # 例データを作成
julia> angles = LinRange(0, 2pi, 40)
julia> radii = LinRange(0, 2, 40)
julia> # 角度と半径をプロット
julia> polar(angles, radii)
julia> # 角度と呼び出し可能な関数をプロット
julia> polar(angles, r -> cos(r) ^ 2)
```
