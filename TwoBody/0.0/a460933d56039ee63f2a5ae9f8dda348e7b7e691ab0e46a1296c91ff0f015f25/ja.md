`SimpleGaussianBasis(a=1)`

!!! note
    この基底は正規化されておらず、s波のみに使用されます。


## 位置空間

$$
\phi_i(\pmb{r}) = \exp(-a_i r^2)
$$

## 運動量空間

$$
\phi_{i}(\pmb{k})  = \frac{1}{(2a_i)^{\frac{3}{2}}} \exp(-k^2/4a_i)
$$

## 証明 (フーリエ変換)

$$
\begin{aligned}
  \phi_{n}(\pmb{k})
  &= \frac{1}{\sqrt{2 \pi}^3}
     \int
     \phi_{n}(\pmb{r})
     \mathrm{e}^{\mathrm{i} \pmb{k} \cdot \pmb{r}}
     \mathrm{d}\pmb{r} \\
  &= \frac{1}{\sqrt{2 \pi}^3}
     \int
     \phi_{n}(\pmb{r})
     \mathrm{e}^{\mathrm{i} \pmb{k} \cdot \pmb{r}} 
     r^2 \sin (\theta)
     ~\mathrm{d}r
     \mathrm{d}\theta
     \mathrm{d} \varphi \\
  &= \frac{1}{\sqrt{2 \pi}^3}
     \iiint
     \mathrm{e}^{-\alpha_i r^2}
     \sqrt{4\pi} Y_{00}(\hat{\pmb{r}})
     \left[
       4 \pi \sum_{l'=0}^{\infty} \sum_{m=-l'}^{l'}
       \mathrm{i}^{l'}
       j_{l'}(pr)
       Y_{l'm'}(\hat{\pmb{k}})
       Y_{l'm'}^*(\hat{\pmb{r}})
     \right]
     r^2 \sin\theta~
     \mathrm{d} r
     \mathrm{d} \theta
     \mathrm{d} \varphi \\
  &= \frac{1}{\sqrt{2 \pi}^3}
     4 \pi \sqrt{4\pi} \sum_{l'=0}^{\infty} \sum_{m=-l'}^{l'} \left[
     \mathrm{i}^{l'}
     Y_{l'm'}(\hat{\pmb{k}})
     \int_0^{2 \pi} 
     \int_0^\pi
       Y_{00}(\hat{\pmb{r}})
       Y_{l'm'}^*(\hat{\pmb{r}})
       \sin (\theta)~
     \mathrm{d} \theta
     \mathrm{d} \varphi
     \int_0^{\infty}
       j_{l'}(pr)
       \mathrm{e}^{-\alpha_i r^2}
       r^{2}
       \mathrm{d}r
     \right]\\
  &=  \frac{1}{\sqrt{2 \pi}^3}
     4 \pi \sqrt{4\pi} \sum_{l'=0}^{\infty} \sum_{m=-l'}^{l'} \left[
     \mathrm{i}^{l'}
     Y_{l'm'}(\hat{\pmb{k}})
     \delta_{0l'}
     \delta_{0m'}
     \int_0^{\infty}
       j_{l'}(kr)
       \mathrm{e}^{-\alpha_i r^2}
       r^{2}
       \mathrm{d}r
     \right] \\
  &= \frac{1}{\sqrt{2 \pi}^3}
     4 \pi \sqrt{4\pi}
     \mathrm{i}^{0}
     Y_{00}(\hat{\pmb{k}})
     \int_0^{\infty}
       j_{0}(kr)
       \mathrm{e}^{-\alpha_i r^2}
       r^{2}
     \mathrm{d}r \\
  &= \frac{1}{2\pi\sqrt{2\pi}}
     4 \pi
     \frac{\sqrt{4\pi}}{\sqrt{4\pi}}
     \sqrt{\frac{\pi}{2}}
     \sqrt{\frac{2}{\pi}}
     \int_0^{\infty}
       j_{0}(kr)
       \mathrm{e}^{-\alpha_i r^2}
       r^{2}
     ~\mathrm{d}r \\
  &= \frac{1}{(2\alpha_i)^{\frac{3}{2}}} \mathrm{e}^{-\frac{k^2}{4 \alpha_i}}
\end{aligned}
$$

## 定理

[球面調和関数における平面波展開](https://en.wikipedia.org/wiki/Plane-wave_expansion#Expansion_in_spherical_harmonics):

$$
\mathrm{e}^{\mathrm{i} \pmb{k} \cdot \pmb{r}}
= 
4 \pi \sum_{l=0}^{\infty} \sum_{m=-l}^{l}
\mathrm{i}^{l}
j_{l}(pr)
Y_{lm}(\hat{\pmb{k}})
Y_{lm}^*(\hat{\pmb{r}})
$$

[球面調和関数の特別な場合](https://en.wikipedia.org/wiki/Spherical_harmonics#List_of_spherical_harmonics):

$$
Y_{00}(\hat{\pmb{r}}) = \frac{1}{\sqrt{4\pi}}
$$

[球面調和関数の直交性](https://en.wikipedia.org/wiki/Spherical_harmonics#Orthogonality_and_normalization):

$$
\int_0^{2\pi}
\int_0^\pi
    Y_{lm}(\hat{\pmb{r}})^*
    Y_{l'm'}(\hat{\pmb{r}})
\sin(\theta) ~
\mathrm{d} \theta
\mathrm{d} \varphi
=
\delta_{ll'}
\delta_{mm'}
$$

引用が必要です:

$$
\sqrt{\frac{2}{\pi}}
\int
r^{l}
j_l(kr)
\mathrm{e}^{-\alpha r^2}
r^{2}
\mathrm{d} r
=
\frac{1}{(2\alpha)^{l+\frac{3}{2}}}
k^l e^{-\frac{k^2}{4\alpha}}
$$
