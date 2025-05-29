```
Call <: CellRule

Cell(f)
Cell{R,W}(f)
```

[`CellRule`](@ref) は、関数 `f` を `R` グリッド値、または値の `Tuple` に適用し、`W` グリッド値または値の `Tuple` を返します。

特に `do` 構文と一緒に使うと便利です。

## 例

グリッド `:a` のセル値を2倍にします：

```jldoctest Cell
using DynamicGrids
simplerule = Cell{:a}() do data, a, I
    2a
end
# output
Cell{:a,:a}(
    f = var"#1#2"
)
```

`data` は [`AbstractSimData`](@ref) オブジェクトで、`a` はセル値、`I` はセルインデックスを保持する `Tuple` です。

複数のグリッド（a と b）を使用する必要がある場合は、`R` と `W` 型パラメータを使用します。外部変数を使用したい場合は、パフォーマンスのために全体を `let` ブロックでラップします。このルールは、`b` の新しい値を `a` の値を `b` 倍したスカラー `y` に設定します：

```jldoctest Cell
y = 0.7
rule = let y = y
    rule = Cell{Tuple{:a,:b},:b}() do data, (a, b), I
        a + b * y
    end
end
# output
Cell{Tuple{:a, :b},:b}(
    f = var"#3#4"{Float64}
)
```
