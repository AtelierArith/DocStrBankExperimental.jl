```
phase_diagram(res::Result{D}; class="physical", not_class=[]) where {D}
```

`Result`オブジェクトから位相図を計算するには、スイープされたパラメータごとに状態の数を合計します。

# キーワード引数

クラス選択は、`String`または`Vector{String}`をkwargとして渡すことで行います：

```
class::String       :   このクラスの解のみをカウントする ("all" --> すべてをプロット)
not_class::String   :   このクラスの解をカウントしない
```

# 戻り値

  * Array{Int64,D}: 指定されたクラスマスクを適用した後の状態の合計
