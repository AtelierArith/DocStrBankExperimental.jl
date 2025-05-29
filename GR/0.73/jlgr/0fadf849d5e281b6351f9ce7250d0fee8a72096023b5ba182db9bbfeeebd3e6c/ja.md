複数のプロットを組み合わせるためのホールドフラグを設定します。

ホールドフラグは、軸の描画や以前のプロットのクリアを防ぎ、次のプロットが前のプロットの上に描画されるようにします。

:param flag: ホールドフラグの値

**使用例:**

.. code-block:: julia

```
julia> # サンプルデータを作成
julia> x = LinRange(0, 1, 100)
julia> # 最初のプロットを描画
julia> plot(x, x.^2)
julia> # ホールドフラグを設定
julia> hold(true)
julia> # 追加のプロットを描画
julia> plot(x, x.^4)
julia> plot(x, x.^8)
julia> # ホールドフラグをリセット
julia> hold(false)
```
