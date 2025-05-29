```
hgcd(a::PolyRingElem{T}, b::PolyRingElem{T}) where T
```

`a` と `b` の半GCDを返します。すなわち、次の条件を満たすタプル `(A, B, m11, m12, m21, m22, s::Int)` を返します。

1. m11*m22 - m12*m21 = s = +-1
2. m11*A + m12*B = a
3. m21*A + m22*B = b
4. `A` と `B` は、`a` を `b` で割ったときの余りの列における連続した余りであり、`deg(A) >= cld(deg(a), 2) > deg(B)` を満たします。
5. `[m11 m12; m21 m22]` は、そのような余り列によって生成された商 `q` に対する `[q 1; 1 0]` の積です。

入力が `degree(a) > degree(b) >= 0` を満たすことを前提としています。

カットオフは現在、非公開関数 `hgcd_prefers_basecase(a, b)` および `mat22_mul_prefers_classical(a11, a12, a21, a22, b11, b12, b21, b22)` によって決定されます。

多項式環の基底環が体でない場合、この関数は NotInvertibleError をスローする可能性があります。それ以外の場合、出力は有効であるべきです。
