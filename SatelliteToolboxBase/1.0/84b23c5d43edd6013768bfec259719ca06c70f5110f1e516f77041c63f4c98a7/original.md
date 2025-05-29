```
KeplerianElements(t::Tepoch, a::T1, e::T2, i::T3, Ω::T4, ω::T5, f::T6)
```

Create an orbit representation using Keplerian elements with semi-major axis `a` [m], eccentricity `e` [ ], inclination `i` [rad], right ascension of the ascending node `Ω` [rad], argument of perigee `ω` [rad], and true anomaly `f` [rad].

The object type is obtained by promoting `T1`, `T2`, `T3`, `T4`, `T5`, and `T6`.
