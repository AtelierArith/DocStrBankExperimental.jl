```
crystalsystem(Rs::DirectBasis{D})  -->  String
crystalsystem(Gs::ReciprocalBasis{D})  -->  String
```

Determine the crystal system of a point lattice with `DirectBasis` `Rs`, assuming the conventional setting choice defined in the International Tables of Crystallography [^ITA6].

If a `ReciprocalBasis` `Gs` is provided for the associated reciprocal point lattice, the crystal system is determined by first transforming to the direct lattice.

There are 4 crystal systems in 2D and 7 in 3D (see Section 2.1.2(iii) of [^ITA5]):

| `D`    |       System |             Conditions |  Free parameters |
|:------ | ------------:| ----------------------:| ----------------:|
| **1D** |       linear |                   none |                a |
| **2D** |       square |            a=b & γ=90° |                a |
|        |  rectangular |                  γ=90° |              a,b |
|        |    hexagonal |           a=b & γ=120° |                a |
|        |      oblique |                   none |            a,b,γ |
| **3D** |        cubic |      a=b=c & α=β=γ=90° |                a |
|        |    hexagonal | a=b & α=β=90° & γ=120° |              a,c |
|        |     trigonal | a=b & α=β=90° & γ=120° | a,c (a,α for hR) |
|        |   tetragonal |        a=b & α=β=γ=90° |              a,c |
|        | orthorhombic |              α=β=γ=90° |            a,b,c |
|        |   monoclinic |                α=γ=90° |      a,b,c,β≥90° |
|        |    triclinic |                   none |      a,b,c,α,β,γ |

The `Rs` must specify a set of conventional basis vectors, i.e., not generally primitive. For primitive basis vectors, the crystal system can be further reduced into 5 Bravais types in 2D and 14 in 3D (see [`bravaistype`](@ref)).

[^ITA6]: M.I. Aroyo, International Tables of Crystallography, Vol. A, 6th ed. (2016): Tables      3.1.2.1 and 3.1.2.2 (or Tables 2.1.2.1, 9.1.7.1, and 9.1.7.2 of [^ITA5]).

[^ITA5]: T. Hahn, International Tables of Crystallography, Vol. A, 5th ed. (2005).
