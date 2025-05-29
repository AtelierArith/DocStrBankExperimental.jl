```
planck_wave(wavelength, temperature) -> black_body_flux
```

### 目的

単位波長あたりの黒体のフラックスを計算します。

### 説明

[プランクの法則](https://en.wikipedia.org/wiki/Planck%27s_law)を使用して、単位波長あたりの黒体のスペクトル放射を返します。

$$
B_λ(λ, T) = \frac{2hc^2}{λ^5} \frac{1}{e^{\frac{hc}{λ k_\mathrm{B}T}} - 1}
$$

### 引数

  * `wavelength`: フラックスを計算する波長（メートル単位）。
  * `temperature`: 黒体の平衡温度（ケルビン単位）。

### 出力

黒体のスペクトル放射（単位は W/(sr·m³)）。

### 例

$$
5000
$$

K で $[0, 3]$ µm の黒体のスペクトルをプロットします。プロットには [Plots.jl](https://github.com/JuliaPlots/Plots.jl/) を使用します。

```julia
using Plots
wavelength = range(0, stop=3e-6, length=1000);
temperature = ones(wavelength)*5000;
flux = planck_wave.(wavelength, temperature);
plot(wavelength, flux)
```

### 注意

`planck_freq` は単位周波数あたりの黒体のフラックスを計算します。

この関数のコードは IDL Astronomy User's Library に基づいています。
