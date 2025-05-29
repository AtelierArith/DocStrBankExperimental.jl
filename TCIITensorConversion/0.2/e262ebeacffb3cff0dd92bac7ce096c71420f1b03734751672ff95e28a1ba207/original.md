```
MPS(tt, siteindices...)
```

Convert a tensor train to an ITensor MPS

  * `tt`            Tensor train
  * `siteindices`   Arrays of ITensor Index objects.

If `siteindices` is left empty, a default set of indices will be used.
