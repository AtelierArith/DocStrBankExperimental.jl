バー プロットを描画します。

特定のラベルが指定されていない場合、軸は 1 から始まる整数でラベル付けされます。

キーワード引数 **barwidth**、**baseline**、または **horizontal** を使用して、バーのデフォルト幅（デフォルトではバー間の間隔の 0.8 倍）、ベースライン値（デフォルトではゼロ）、またはバーの方向（デフォルトでは垂直）を変更できます。

:param labels: バーのラベル :param heights: バーの高さ

**使用例:**

.. code-block:: julia

```
julia> # 大陸別の世界人口（百万）
julia> population = Dict("Africa" => 1216,
                         "America" => 1002,
                         "Asia" => 4436,
                         "Europe" => 739,
                         "Oceania" => 38)
julia> barplot(keys(population), values(population))
julia> # 水平バー プロット
julia> barplot(keys(population), values(population), horizontal=true)
```
