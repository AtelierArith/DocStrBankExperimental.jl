```
maxyearspan(A::ClimArray) = maxyearspan(dims(A, Time))
maxyearspan(t::AbstractVector{<:DateTime}) → i
```

Find the maximum index `i` of `t` so that `t[1:i]` covers exact(*) multiples of years.

(*) For monthly spaced data `i` is a multiple of `12` while for daily data we find the largest possible multiple of `DAYS_IN_ORBIT`.
