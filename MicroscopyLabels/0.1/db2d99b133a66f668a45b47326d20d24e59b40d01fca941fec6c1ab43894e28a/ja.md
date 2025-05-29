```
timestamp!(img; units)
```

マルチディメンショナル画像 `img` の左上隅に、単位 `units` でタイムスタンプを書き込みます。画像には、少なくとも `x`、`y`、および `time` 軸がラベル付けされている必要があります。つまり、`img` は `xyt` 軸を持つ `AxisArray` オブジェクトである必要があります。追加の軸が存在する場合、タイムスタンプはすべての軸に書き込まれます。

### 簡単な例

```jldoctest ex; output = false
using AxisArrays
using MicroscopyLabels

tmp = AxisArray(zeros(200, 200, 5), Axis{:x}(1:200), Axis{:y}(1:200), Axis{:time}(1:5))
timestamp!(tmp)

# output


```

### 単位付きの例

時間軸に単位を追加し、これを画像に埋め込むこともできます。

```jldoctest ex; output=false
using Unitful: s, minute

tmp = AxisArray(zeros(200, 200, 5), Axis{:x}(1:200), Axis{:y}(1:200),
                Axis{:time}(0s:45.0s:180s))
# 単位を分に変換
timestamp!(tmp, units=minute)

# output


```
