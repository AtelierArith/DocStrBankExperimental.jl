```
timestamp!(img; units)
```

Writes the timestamp in the upper left corner of a multidimensional image `img` with the units `units`. Images are required to have at least the `x`, `y`, and `time` axes labeled, i.e. `img` should be or contain an `AxisArray` object with xyt axes. If additional axes are present, the timestamp will be written to all of them.

### Simple example

```jldoctest ex; output = false
using AxisArrays
using MicroscopyLabels

tmp = AxisArray(zeros(200, 200, 5), Axis{:x}(1:200), Axis{:y}(1:200), Axis{:time}(1:5))
timestamp!(tmp)

# output


```

### Unitful example

We can also add units to the time axis and have these be embedded in the image

```jldoctest ex; output=false
using Unitful: s, minute

tmp = AxisArray(zeros(200, 200, 5), Axis{:x}(1:200), Axis{:y}(1:200),
                Axis{:time}(0s:45.0s:180s))
# convert the units to minutes
timestamp!(tmp, units=minute)

# output


```
