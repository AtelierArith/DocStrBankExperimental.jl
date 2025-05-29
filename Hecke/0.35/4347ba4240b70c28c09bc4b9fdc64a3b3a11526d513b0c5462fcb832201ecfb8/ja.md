```
disc_log(P::EllipticCurvePoint, Q::EllipticCurvePoint, [n::IntegerUnion]) -> ZZRingElem
```

$$
P
$$

に関する$Q$の離散対数$m$を返します。すなわち、$mP = Q$です。

$$
P
$$

の順序の倍数$n$が知られている場合、これはオプションの引数として指定できます。

```jldoctest
julia> E = elliptic_curve(GF(101), [1, 2]);

julia> P = E([6, 74])
(6 : 74 : 1)

julia> Q = E([85, 43])
(85 : 43 : 1)

julia> disc_log(P, Q)
13
```
