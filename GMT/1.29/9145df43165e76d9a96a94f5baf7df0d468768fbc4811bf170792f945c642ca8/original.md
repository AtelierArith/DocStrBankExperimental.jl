```
I = ind2rgb(I::GMTimage, cpt::GMTcpt=GMTcpt(), layout="BRPa"; cmap=GMTcpt())
```

Convert an indexed image I to RGB. If `cmap` is not provided, it uses the internal colormap to do the conversion. If neither them exists, the layer is replicated 3 times thus resulting in a gray scale image.

Use the `cmap` keyword in alternative to the `cpt` positional variable. 
