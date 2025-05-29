プロット軸にグリッドを描画するためのフラグを設定します。

:param flag: グリッドフラグの値（デフォルトは`true`）

**使用例:**

.. code-block:: julia

```
julia> # 次のプロットでグリッドを非表示にする
julia> grid(false)
julia> # グリッドを復元する
julia> grid(true)
```
