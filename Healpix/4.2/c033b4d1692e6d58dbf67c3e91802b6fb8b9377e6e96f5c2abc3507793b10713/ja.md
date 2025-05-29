```
pix2ringpos(resol::Resolution, pixel)
```

Healpixマップのリング順でのピクセルの（1ベースの）インデックスを与えると、次の意味を持つ数のペア（n, i, j）を返します：

  * `n` は、空の領域を表すシンボル `:northcap`、 `:equator`、または `:southcap` のいずれかです
  * `i` は、1から 4NSIDE - 1 までのリングインデックスです
  * `j` は、リング内のピクセルインデックスです
