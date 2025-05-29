プロットのタイトルを設定します。

プロットのタイトルは、拡張テキスト関数GR.textextを使用して描画されます。LaTeXの数式構文のサブセットを使用できますが、特定の文字（例えば、括弧）をエスケープする必要があります。詳細については、GR.textextのドキュメントを参照してください。

:param title: プロットのタイトル

**使用例:**

.. code-block:: julia

```
julia> # プロットのタイトルを "Example Plot" に設定
julia> title("Example Plot")
julia> # プロットのタイトルをクリア
julia> title("")
```
