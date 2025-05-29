ヒストグラムを描画します。

**nbins** が **nothing** または 0 の場合、この関数はビンの数を 3.3 * log10(n) + 1 と計算します。ここで n は x の要素数です。それ以外の場合は、指定されたビンの数がヒストグラムに使用されます。

:param x: ヒストグラムとして描画する値 :param num_bins: ヒストグラムのビンの数

**使用例:**

.. code-block:: julia

```
julia> # サンプルデータを作成
julia> x = 2 .* rand(100) .- 1
julia> # ヒストグラムを描画
julia> histogram(x)
julia> # 19 ビンでヒストグラムを描画
julia> histogram(x, nbins=19)
```
