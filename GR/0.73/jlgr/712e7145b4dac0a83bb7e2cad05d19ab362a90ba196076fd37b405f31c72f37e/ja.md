ヒートマップを描画します。

この関数は、現在のカラーマップを使用して二次元配列をヒートマップとして表示します。配列はその最初の値が左下隅に描画されるため、場合によっては列を反転させる必要があるかもしれません（下の例を参照）。

デフォルトでは、関数はx軸とy軸にそれぞれ列インデックスと行インデックスを使用するため、軸の制限を設定することをお勧めします。また、配列内の値は現在のz軸の制限内に収まる必要があるため、これらの制限を調整するか、配列の値の範囲をクリップする必要があるかもしれません。

:param data: ヒートマップデータ

**使用例:**

.. code-block:: julia

```
julia> # 例のデータを作成
julia> x = LinRange(-2, 2, 40)
julia> y = LinRange(0, pi, 20)
julia> z = sin.(x') .+ cos.(y)
julia> # ヒートマップを描画
julia> heatmap(z)
```
