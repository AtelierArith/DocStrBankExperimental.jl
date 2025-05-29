```
gaunt_coefficient(l1,m1,l2,m2,l3,m3)
```

A version of the Gaunt coefficients which are used to write the product of two spherical harmonics. If Y_{l,m} is a complex spherical harmonic, with the typical phase conventions from quantum mechanics, then:

```
gaunt_coefficient(l1,m1,l2,m2,l3,m3) = 4*π*im^{l2+l3-l1} Integral[Y_{l1,m1}*conj(Y_{l2,m2})*conj(Y_{l3,m3})]
```

where the integral is over the solid angle.

The most standard gaunt coefficients `G(l1,m1;l2,m2;l3)` are related through the identity:

```
4pi * G(l1,m1;l2,m2;l3) = im^(l1-l2-l3) * (-1)^m2 * gaunt_coefficient(l1,m1,l2,-m2,l3,m1+m2)
```
