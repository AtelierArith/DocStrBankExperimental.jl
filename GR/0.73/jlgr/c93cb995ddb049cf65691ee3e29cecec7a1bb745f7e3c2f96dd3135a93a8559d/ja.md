x軸のラベルを設定します。

軸ラベルは、拡張テキスト関数GR.textextを使用して描画されます。LaTeX数式構文のサブセットを使用できますが、特定の文字（例えば、括弧）をエスケープする必要があります。詳細については、GR.textextのドキュメントを参照してください。

:param x_label: x軸のラベル

**使用例:**

.. code-block:: julia

```
julia> # x軸のラベルを"x"に設定
julia> xlabel("x")
julia> # x軸のラベルをクリア
julia> xlabel("")
```
