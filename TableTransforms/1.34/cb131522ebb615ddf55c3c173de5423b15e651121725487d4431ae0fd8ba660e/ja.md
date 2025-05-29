```
Unit(unit)
```

テーブル内のすべての列の単位を Unitful.jl の `unit` に変換します。

```
Unit(cols₁ => unit₁, cols₂ => unit₂, ..., colsₙ => unitₙ)
```

選択した列 `cols₁`, `cols₂`, ..., `colsₙ` の単位を `unit₁`, `unit₂`, ... `unitₙ` に変換します。

単位のない列は、明示的に選択されると単位を持つようになります。

# 例

```julia
Unit(u"m")
Unit(1 => u"km", :b => u"K", "c" => u"s")
Unit([2, 3] => u"cm")
Unit([:a, :c] => u"cm")
Unit(["a", "c"] => u"cm")
Unit(r"[abc]" => u"km")
```
