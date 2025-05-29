```
CBF_maxgrad(tseries::ImageMeta[;positionArtery=[1,1,1], alpha=0.4, alpha2=2,windowsize=6])
```

Calculates the maximum gradient pixelwise along temporal dimension for pixels inside the mask and divides by maximum concentration at the position of the artery. Alternative: CBF which calculates the cerebral blood flow from the ratio CBV/MTT
