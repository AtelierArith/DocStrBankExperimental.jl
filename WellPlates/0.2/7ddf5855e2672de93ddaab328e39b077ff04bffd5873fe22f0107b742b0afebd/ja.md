```
ingredients(plate[, condition::Symbol])
ingredients(plate, group => value)
```

プレートを構築するための物理的要件の `Dict` を取得します。数値条件は合計され、非数値はカウントされます。

## グルーピング

要因を別の条件として格納する場合、特別な構文を使用してこれを指定できます。

### 例

```jldoctest
julia> p = plate(96, volume = 100μL, cells = down([:Raji, :DG75], FillLast));
julia> ingredients(p, :cells => :volume)[:Raji]
1200 μL
```
