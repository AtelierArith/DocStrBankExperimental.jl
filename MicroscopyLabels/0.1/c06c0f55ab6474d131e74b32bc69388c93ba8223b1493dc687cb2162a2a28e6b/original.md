```
scalebar!(img, len; fontsize)
```

Add a scalebar `len` long in the bottom left of `img` along the x axis with text of size `fontsize` given as a fraction of the smallest spatial axis.

## Example

```jldoctest; output=false
using Unitful: μm
using AxisArrays
using MicroscopyLabels

tmp = AxisArray(zeros(200, 200), Axis{:y}(1μm:1μm:200μm), Axis{:x}(1μm:1μm:200μm));

scalebar!(tmp, 25μm, fontsize=0.06)

# output


```
