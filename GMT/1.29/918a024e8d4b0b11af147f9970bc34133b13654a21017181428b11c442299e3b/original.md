crop(arg::GItype; kw...)

Crop a subregion of a grid (GMTgrid) or a image (GMTimage).

The subregion is specified with the $limits$ or $region$ keyword; the specified range must not exceed the range of the input.  This function differs from $grdcut$ in the sense that it doesn't call the GMT lib and works only on in-memory array (i.e., no disk files).

### Returns

A grid or an image, depending on the input type, plus two 1x2 matrices with the indices of the cropped zone.

## Example

```
G = GMT.peaks();
crop(G, region=(-2,2,-2,2))
```
