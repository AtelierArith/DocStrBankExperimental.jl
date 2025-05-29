```
planck_freq(frequency, temperature) -> black_body_flux
```

### 目的

周波数あたりの黒体のフラックスを計算します。

### 説明

[プランクの法則](https://en.wikipedia.org/wiki/Planck%27s_law)を使用して、周波数あたりの黒体のスペクトル放射を返します。

$$
B_\nu(\nu, T) = \frac{2h\nu^3}{c^2} \frac{1}{e^\frac{h\nu}{k_\mathrm{B}T} - 1}
$$

### 引数

  * `frequency`: フラックスを計算する周波数（ヘルツ単位）。
  * `temperature`: 黒体の平衡温度（ケルビン単位）。

### 出力

黒体のスペクトル放射（単位は W/(sr·m²·Hz)）。

### 例

8000 Kで$[10^{12}, 10^{15.4}]$ Hzの黒体のスペクトルをプロットします。プロットには[Plots.jl](https://github.com/JuliaPlots/Plots.jl/)を使用します。

```julia
using Plots
frequency = exp10.(range(12, stop=15.4, length=1000));
temperature = ones(size(frequency)) * 8000;
flux = planck_freq.(frequency, temperature);
plot(frequency, flux)
```

### 注意

`planck_wave`は、波長あたりの黒体のフラックスを計算します。
