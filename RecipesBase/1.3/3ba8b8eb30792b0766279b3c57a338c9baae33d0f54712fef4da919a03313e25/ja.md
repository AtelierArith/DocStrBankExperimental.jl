```
@layout mat
```

シンボルの行列からサブプロットのレイアウトを生成します（サブプロットは複数の行または列にまたがることができます）。正確なサイズ設定は波括弧を使用して達成できます。それ以外の場合、空いているスペースはサブプロットのプロット領域の間で均等に分割されます。レイアウト内のプロットを無視するには、`_`（アンダースコア）文字を使用できます（空白のプロット）。

# 例

```julia-repl
julia> @layout [a b; c]
2×1 Matrix{Any}:
 Any[(label = :a, blank = false) (label = :b, blank = false)]
 (label = :c, blank = false)

julia> @layout [a{0.3w}; b{0.2h}]
2×1 Matrix{Any}:
 (label = :a, width = 0.3, height = :auto)
 (label = :b, width = :auto, height = 0.2)

julia> @layout [_ ° _; ° ° °; ° ° °]
3×3 Matrix{Any}:
 (label = :_, blank = true)   …  (label = :_, blank = true)
 (label = :°, blank = false)     (label = :°, blank = false)
 (label = :°, blank = false)     (label = :°, blank = false)

```
