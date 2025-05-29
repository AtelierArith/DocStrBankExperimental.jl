三次元ワイヤーフレームプロットを描画します。

この関数は、現在のカラーマップを使用して、ポイントの系列または二次元配列をワイヤーフレームプロットとして表示します。以下のいずれかを受け取ることができます：

  * x 値、y 値、z 値、または
  * M x 値、N y 値、および NxM グリッド上の z 値、または
  * M x 値、N y 値、および z 値を決定するための呼び出し可能な関数

この関数にポイントの系列が渡されると、それらの値はグリッド上で補間されます。提供されたポイントの凸包の外側にあるグリッドポイントには、0 の値が使用されます。

:param args: プロットするデータ

**使用例：**

.. code-block:: julia

```
julia> # 例のポイントデータを作成
julia> x = 8 .* rand(100) .- 4
julia> y = 8 .* rand(100) .- 4
julia> z = sin.(x) .+ cos.(y)
julia> # ワイヤーフレームプロットを描画
julia> wireframe(x, y, z)
julia> # 例のグリッドデータを作成
julia> x = LinRange(-2, 2, 40)
julia> y = LinRange(0, pi, 20)
julia> z = sin.(x') .+ cos.(y)
julia> # ワイヤーフレームプロットを描画
julia> wireframe(x, y, z)
julia> # 呼び出し可能な関数を使用してワイヤーフレームプロットを描画
julia> wireframe(x, y, (x,y) -> sin(x) + cos(y))
```
