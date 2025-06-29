```
surface([x, y,] z; kwargs...)
```

三次元サーフェスプロットを描画します。

一連の点または二次元配列がサーフェスプロットとして描画され、Z座標と現在のカラーマップに従って色付けされます。次のいずれかを受け取ることができます：

  * `x` 値、`y` 値、および `z` 値。
  * *M* のソートされた `x` 軸の値、*N* のソートされた `y` 軸の値、および *N*×*M* グリッド上の `z` 値のセット。
  * *M* のソートされた `x` 軸の値、*N* のソートされた `y` 軸の値、および `z` 値を決定するための呼び出し可能な関数。
  * *N*×*M* グリッド上の `z` 値で、*x* および *y* 軸はそれぞれグリッドの列と行のインデックスとして定義されます。

この関数に一連の点が渡されると、それらの値はグリッド上で補間されます。提供された点の凸包の外側にあるグリッドポイントには、0の値が使用されます。

# 例

```julia
# 例のグリッドデータを作成
x = LinRange(-2, 2, 40)
y = LinRange(0, pi, 20)
z = sin.(x') .+ cos.(y)
# サーフェスプロット
surface(x, y, z)

```
