```
intersectionlines(p0, p1, p2, p3;
    crossingonly=false)
```

2つの線が交差する点を見つけます。

`(resultflag, resultip)`を返します。ここで、`resultflag`はBooleanで、`resultip`はPointです。

`crossingonly == true`の場合、交差点は両方の線上に存在しなければなりません。

`crossingonly == false`の場合、交差点は線がほぼ「無限」に延長されたときに出会う場所であっても構いません。

この関数によれば、共線、重なり、平行な線は決して交差しません。つまり、線分は共線であるが共通の点を持たない場合や、線分は共線であり多くの共通点を持つ場合、または線分は共線であり一方が完全に他方に含まれている場合があります。

線が共線であり、共通の点を持つ場合、それが交差点です。
