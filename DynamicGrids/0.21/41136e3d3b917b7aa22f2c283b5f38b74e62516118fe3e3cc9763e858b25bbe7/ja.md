```
add!(data::WritableGridData, x, I...)
```

グリッドセルに値 `x` を追加します。

## 使用例

```jldoctest
using DynamicGrids
rule = SetCell{:a}() do data, a, cellindex
    dest, is_inbounds = inbounds(data, (jump .+ cellindex)...)

    # グリッド上にある場合は、スポットされたセルを更新します
    is_inbounds && add!(data[:a], state, dest...)
end

# 出力
SetCell{:a,:a}(
    f = var"#1#2"
)
```
