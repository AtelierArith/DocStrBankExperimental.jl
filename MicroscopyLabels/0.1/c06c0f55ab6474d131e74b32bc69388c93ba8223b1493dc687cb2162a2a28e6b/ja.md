```
scalebar!(img, len; fontsize)
```

画像 `img` の左下に x 軸に沿って `len` の長さのスケールバーを追加し、最小の空間軸の割合として与えられたサイズ `fontsize` のテキストを表示します。

## 例

```jldoctest; output=false
using Unitful: μm
using AxisArrays
using MicroscopyLabels

tmp = AxisArray(zeros(200, 200), Axis{:y}(1μm:1μm:200μm), Axis{:x}(1μm:1μm:200μm));

scalebar!(tmp, 25μm, fontsize=0.06)

# output


```
