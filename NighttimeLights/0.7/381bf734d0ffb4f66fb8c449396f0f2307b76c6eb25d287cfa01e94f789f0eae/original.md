A mask can be applied to a datacube cube so that each image of the datacube has 0s wherever the mask is dark and the original value wherever the mask is lit. 

# Example:

```
datacube = rand(1:10.0, 10,10,10)
mask = rand(0:1, 10, 10)
apply_mask(datacube, mask)
```
