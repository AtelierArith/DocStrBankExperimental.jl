```
ExCaliber(
    axon::Cylinder,
    extra::Zeppelin,
    dot::Iso,
    fracs::Vector{Float64}
    )
```

ExCaliberは、軸索の直径を推定するための多区画モデルです。ISO区画の拡散率が0（ドット区画）に設定されている場合、ex vivoイメージングに使用でき、ISO区画の拡散率が組織内の自由水（CSF区画）に設定されている場合にはin vivoイメージングに使用できます。

# 参考文献

Gong, T., Maffei, C., Dann, E., Lee, H.-H., Lee, H., Augustinack, J.C., Huang, S.Y., Haber, S.N., Yendiki, A., 2025. Interplay between MRI-based axon diameter and myelination estimates in macaque and human brain. Imaging Neuroscience. https://doi.org/10.1162/IMAG*A*00576

Fan, Q., Nummenmaa, A., Witzel, T., Ohringer, N., Tian, Q., Setsompop, K., ... & Huang, S. Y. (2020). Axon diameter index estimation independent of fiber orientation distribution using high-gradient diffusion MRI. Neuroimage, 222, 117197.
