```
skeletonize(R) → R_skel
```

`RecurrenceMatrix R`をKraemer & Marwanによって提案されたアルゴリズムを使用してスケルトン化します[^Kraemer2019]。この関数は、"厚さ"が1の対角線のみで構成される再発行列`R_skel`を返します。

[^Kraemer2019]: Kraemer, K.H., Marwan, N. (2019). [Border effect corrections for diagonal line based recurrence quantification analysis measures. Physics Letters A 383(34)](https://doi.org/10.1016/j.physleta.2019.125977).
