```
label_particles!(img, labels)
```

`ImageMorphology.label_components`によって生成されたテキストラベルを`img`に書き込みます。`ImageMorphology.component_centroids`によって特定された各重心に対して1つのテキストラベルを書き込みます。背景ピクセル、すなわち0でラベル付けされたものは無視されます。

### 例

```jldoctest; output=false
using MicroscopyLabels
using AxisArrays
using ImageMorphology

# 1つのスポットを持つ50x50x1のYXT画像を作成
img = AxisArray(zeros(50, 50, 1), Axis{:y}(1:50), Axis{:x}(1:50), Axis{:time}(1:1));
img[10:12, 10:12, 1:1] .= 1.0;

# ImageMorphology.label_componentsを使用してラベルを割り当て
labels = AxisArray(label_components(img .!== 0.0), AxisArrays.axes(img));

label_particles!(img, labels)

# 出力

```
