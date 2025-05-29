```
SetGrid{R,W}(f)
```

関数 `f` を適用して、全体のグリッドを埋めます。

ブロードキャスティングは値を更新する良い方法です。

## 例

この例では、グリッド `a` をグリッド `b` に等しく設定します：

```jldoctest
using DynamicGrids
rule = SetGrid{:a,:b}() do a, b
    b .= a
end

# output
SetGrid{:a,:b}(
    f = var"#1#2"
)
```
