```
inpolygon(p, poly)
inpolygon(p, poly, [::MembershipCheckAlgorithm])
inpolygon(p, poly, [::MembershipCheckAlgorithm]; in = 1, on = -1, out = 0)
```

check the membership of `p` in `poly` where `poly` is an `AbstractVector` of `AbstractVector`s. `poly` should have the first and last elements equal.

*Returns:*

  * in = 1
  * on = -1
  * out = 0

*MembershipCheckAlgorithm:*

  * `HaoSun()`
  * `HormannAgathos()`

Default is `HaoSun()` as it has the best performance and works invariant of winding order and self-intersections. However the HaoSun algorithm is new and bugs may be possible. The classic HormannAgathos algorithm is provided, however it is sensitive to self-intersections and winding order so may produce different results.

*Custom return values:*

The return logic can be customized to return alternate values and types by specify the `in`, `on`, and `out` keywords. For example, to treat the 'on' and 'in' cases the same and return a `Bool`: `inpolygon(p, poly, in=true, on=true, out=false)`

Algorithm by Hao and Sun (2018): https://doi.org/10.3390/sym10100477

Hormann-Agathos (2001) Point in Polygon algorithm: https://doi.org/10.1016/S0925-7721(01)00012-8
