X軸とY軸の目盛ラベルの文字列をカスタマイズします。

目盛軸のラベルは、1つの引数（目盛位置の数値）を持つ関数を通じて定義され、その関数は文字列を返すか、X = 1, 2, などに順次配置される文字列の配列を通じて定義できます。

:param s: 目盛ラベルを定義する関数または文字列の配列。

**使用例:**

.. code-block:: julia

```
julia> # Y軸の範囲(0-1)をパーセント値としてラベル付け
julia> yticklabels(p -> Base.Printf.@sprintf("%0.0f%%", 100p))
julia> # X軸を文字列のシーケンスでラベル付け
julia> xticklabels(["first", "second", "third"])
```
