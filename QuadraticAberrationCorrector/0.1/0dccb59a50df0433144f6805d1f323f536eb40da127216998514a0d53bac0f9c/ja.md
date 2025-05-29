```
WeightedCorrectAberration(ϕ, ρx, ρy)
```

重み付き最小二乗アルゴリズムを使用して、`ϕ`の補正された位相マップを返します。引数`ρx`と`ρy`は分割数です。入力位相マップ`ϕ`は、最大-最小-平均-標準偏差（MMASD）メトリックに基づいて重み付き行列を取得するために、$\rho_{x}\times\rho_{y}$グリッドに分割されます。詳細については、以下の参考文献を参照してください。

> [Zhenkai Chen, Wenjing Zhou, Lian Duan, Hongbo Zhang, Huadong Zheng, Xinxing Xia, Yingjie Yu, and Ting-chung Poon, "Automatic elimination of phase aberrations in digital holography based on Gaussian 1σ- criterion and histogram segmentation," Opt. Express **31**, 13627-13639 (2023)](https://doi.org/10.1364/OE.486890)

