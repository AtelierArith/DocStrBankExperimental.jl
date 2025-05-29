```
default_scitype_check_level()
```

マシンを構築する際の科学的型チェックの現在のグローバルデフォルト値を返します。

```
default_scitype_check_level(i::Integer)
```

科学的型チェックのグローバルデフォルト値を `i` に設定します。

`machine(model, data, scitype_check_level=...)` の形式での呼び出しにおける `scitype_check_level` オプションの効果は以下の通りです：

| `scitype_check_level` | scitypesを検査しますか？ | scitypesに`Unknown`がある場合 | 他のscitypeの不一致の場合 |
|:--------------------- |:----------------:|:-----------------------:|:----------------:|
| 0                     |        ×         |                         |                  |
| 1 (起動時の値)             |        ✓         |                         |        警告        |
| 2                     |        ✓         |           警告            |        警告        |
| 3                     |        ✓         |           警告            |       エラー        |
| 4                     |        ✓         |           エラー           |       エラー        |

[`machine`](@ref) も参照してください。
