```
propagator(particle::AbstractParticleType, mom::QEDbase.AbstractFourMomentum)
```

与えられた四運動量 `mom` に対する粒子のプロパゲーターを計算します。

# 規約に関する注意

`QEDProcesses.jl` パッケージには、2種類のプロパゲーターが含まれています。

**ボソン様粒子**: 四運動量 `k` と質量 `m = QEDbase.mass(particle)` を持つ `BosonLike` 粒子の場合、プロパゲーターは次のように与えられます。

$$
D(k) = \frac{1}{k^2 - m^2}
$$

**フェルミオン様粒子**: 四運動量 `p` と質量 `m = QEDbase.mass(particle)` を持つ `FermionLike` 粒子の場合、プロパゲーターは次のように定義されます。

$$
S(p) = \frac{\gamma^\mu p_\mu + m}{p^2 - m^2}
$$

ここで、$\gamma^\mu$ はガンマ行列であり、$p_\mu$ は四運動量成分を表します。

!!! warning
    この関数は、粒子がオフシェルである場合（すなわち、質量シェル条件を満たさない場合）にエラーをスローしません。そのような場合、関数は `Inf` を返し、これはオフシェル粒子に対してプロパゲーターが未定義であることを示します。

