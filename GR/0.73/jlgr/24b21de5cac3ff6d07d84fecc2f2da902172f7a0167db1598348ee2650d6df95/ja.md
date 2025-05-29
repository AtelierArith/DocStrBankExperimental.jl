現在のプロットを再描画

これは、タイトル、軸ラベル、凡例などの属性を設定した後に現在のプロットを更新するために使用できます。

**使用例:**

.. code-block:: julia-repl

```
julia> # 例データを作成
julia> x = LinRange(-2, 2, 40)
julia> y = 2 .* x .+ 4
julia> # タイトルとラベルを追加
julia> title("例のプロット")
julia> xlabel("x")
julia> ylabel("y")
julia> # 新しい属性でプロットを再描画
julia> redraw()
```
