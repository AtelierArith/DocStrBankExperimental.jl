```
propagator(particle::AbstractParticleType, mom::QEDbase.AbstractFourMomentum)
```

与えられた四モーメント `mom` に対する粒子のプロパゲーターを計算します。

# 規約に関する注意

`QEDProcesses.jl` パッケージには、2種類のプロパゲーターが含まれています。

**ボソン様粒子**: 四モーメント `k` と質量 `m = QEDbase.mass(particle)` を持つ `BosonLike` 粒子の場合、プロパゲーターは次のように与えられます。

$$
D(k) = \frac{1}{k^2 - m^2}
$$

**フェルミオン様粒子**: 四モーメント `p` と質量 `m = QEDbase.mass(particle)` を持つ `FermionLike` 粒子の場合、プロパゲーターは次のように定義されます。

$$
S(p) = \frac{\gamma^\mu p_\mu + m}{p^2 - m^2}
$$

ここで、$\gamma^\mu$ はガンマ行列であり、$p_\mu$ は四モーメントの成分を表します。

!!! warning
    この関数は、粒子がオフシェルである場合（すなわち、質量シェル条件を満たさない場合）にエラーをスローしません。そのような場合、関数は `Inf` を返し、これはオフシェル粒子に対してプロパゲーターが未定義であることを示します。

