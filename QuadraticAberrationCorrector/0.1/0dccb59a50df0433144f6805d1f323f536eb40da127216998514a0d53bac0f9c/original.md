```
WeightedCorrectAberration(ϕ, ρx, ρy)
```

Return the corrected phase map of `ϕ` using the weighted least squares algorithm. Argument `ρx` and `ρy` are division numbers. The input phase map `ϕ` is divided into a $\rho_{x}\times\rho_{y}$ grid to obtain a weighted matrix based on the maximum-minimum-average-standard deviation (MMASD) metric. See the following reference for details.

> [Zhenkai Chen, Wenjing Zhou, Lian Duan, Hongbo Zhang, Huadong Zheng, Xinxing Xia, Yingjie Yu, and Ting-chung Poon, "Automatic elimination of phase aberrations in digital holography based on Gaussian 1σ- criterion and histogram segmentation," Opt. Express **31**, 13627-13639 (2023)](https://doi.org/10.1364/OE.486890)

