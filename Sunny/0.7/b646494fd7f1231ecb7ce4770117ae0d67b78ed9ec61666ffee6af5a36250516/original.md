```
FormFactor(ion::String; g_lande=2)
```

The magnetic form factor for a given magnetic ion and charge state. When passed to [`intensities`](@ref), it rescales structure factor intensities based on the magnitude of the scattering vector, $|𝐪|$.

The parameter `ion` must be one of the following strings:

```
Am2, Am3, Am4, Am5, Am6, Am7, Au1, Au2, Au3, Au4, Au5, Ce2, Co0, Co1, Co2, Co3,
Co4, Cr0, Cr1, Cr2, Cr3, Cr4, Cu0, Cu1, Cu2, Cu3, Cu4, Dy2, Dy3, Er2, Er3, Eu2,
Eu3, Fe0, Fe1, Fe2, Fe3, Fe4, Gd2, Gd3, Hf2, Hf3, Ho2, Ho3, Ir0a, Ir0b, Ir0c,
Ir1a, Ir1b, Ir2, Ir3, Ir4, Ir5, Ir6, Mn0, Mn1, Mn2, Mn3, Mn4, Mn5, Mo0, Mo1, Nb0,
Nb1, Nd2, Nd3, Ni0, Ni1, Ni2, Ni3, Ni4, Np3, Np4, Np5, Np6, Os0a, Os0b, Os0c,
Os1a, Os1b, Os2, Os3, Os4, Os5, Os6, Os7, Pd0, Pd1, Pr3, Pt1, Pt2, Pt3, Pt4,
Pt5, Pt6, Pu3, Pu4, Pu5, Pu6, Re0a, Re0b, Re0c, Re1a, Re1b, Re2, Re3, Re4, Re5,
Re6, Rh0, Rh1, Ru0, Ru1, Sc0, Sc1, Sc2, Sm2, Sm3, Ta2, Ta3, Ta4, Tb2, Tb3, Tc0,
Tc1, Ti0, Ti1, Ti2, Ti3, Tm2, Tm3, U3, U4, U5, V0, V1, V2, V3, V4, W0a, W0b,
W0c, W1a, W1b, W2c, W3, W4, W5, Y0, Yb2, Yb3, Zr0, Zr1
```

The trailing number denotes ionization state. For example, `"Fe0"` denotes a neutral iron atom, while `"Fe2"` denotes `Fe²⁺`. If multiple electronic configurations are possible, they will be distinguished by a trailing letter (`a`, `b`, ...). Omitting this letter will print an informative error,

```
FormFactor("Ir0")

ERROR: Disambiguate form factor according to electronic configuration:
    "Ir0a" -- 6s⁰5d⁹
    "Ir0b" -- 6s¹5d⁸
    "Ir0c" -- 6s²5d⁷
```

In the dipolar approximation (small $|𝐪|$) the form factor is

$F(s) = ⟨j_0(s)⟩ + [(2-g)/g] ⟨j_2(s)⟩$,

involving $s = |𝐪|/4π$ and the Landé $g$-factor. The $⟨j_l(s)⟩$ are radial averages of the $l$th spherical Bessel function of the magnetic dipole. More details are provided in Ref. [1].

The standard approximation tables involve expansion in Gaussians,

$$
⟨j_0(s)⟩ = A e^{-as^2} + B e^{-bs^2} + C e^{-cs^2} + D e^{-ds^2} + E
$$

and

$$
⟨j_2(s)⟩ = (A e^{-as^2} + B e^{-bs^2} + C e^{-cs^2} + D e^{-ds^2} + E) s^2.
$$

For 3d, 4d, rare earth, and actinide ions, Sunny uses the revised tables of P. J. Brown, as documented in the McPhase package [2]. For 5d ions, Sunny uses the tables of Kobayashi, Nagao, Ito [3].

Two special, $𝐪$-independent form factor values are available: `one(FormFactor)` and `zero(FormFactor)`. The first idealizes the magnetic ion as a perfect point particle, while the second zeros all contributions from the magnetic ion.

## References

1. [P. J. Brown, The Neutron Data Booklet, 2nd ed., Sec. 2.5 *Magnetic Form Factors* (2003)](https://www.ill.eu/sites/ccsl/ffacts/ffachtml.html).
2. Coefficient tables in [McPhase documentation](https://www2.cpfs.mpg.de/~rotter/homepage_mcphase/manual/node137.html).
3. [K. Kobayashi, T. Nagao, M. Ito, *Radial integrals for the magnetic form factor of 5d transition elements*, Acta Cryst. A, **67**, 473–480 (2011)](https://doi.org/10.1107/S010876731102633X).
