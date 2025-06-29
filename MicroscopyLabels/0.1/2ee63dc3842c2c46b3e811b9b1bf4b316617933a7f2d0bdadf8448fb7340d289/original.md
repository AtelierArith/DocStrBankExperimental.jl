```
label_particles!(img, labels)
```

Writes text labels generated by `ImageMorphology.label_components` into `img`. Writes one text label per centroid identified by `ImageMorphology.component_centroids`. Ignores the background pixels, i.e. anything labeled with 0.

### Example

```jldoctest; output=false
using MicroscopyLabels
using AxisArrays
using ImageMorphology

# create a 50x50x1 YXT image with one spot
img = AxisArray(zeros(50, 50, 1), Axis{:y}(1:50), Axis{:x}(1:50), Axis{:time}(1:1));
img[10:12, 10:12, 1:1] .= 1.0;

# assign labels using ImageMorphology.label_components
labels = AxisArray(label_components(img .!== 0.0), AxisArrays.axes(img));

label_particles!(img, labels)

# output

```
