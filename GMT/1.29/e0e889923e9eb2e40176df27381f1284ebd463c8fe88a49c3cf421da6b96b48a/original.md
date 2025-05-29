```
p = polyfit(x, y, n=length(x)-1; xscale=1)
```

Returns the coefficients for a polynomial p(x) of degree `n` that is the least-squares best fit for the data in y. The coefficients in p are in ascending powers, and the length of p is n+1.

The `xscale` parameter is useful when needing to get coeficients in different x units. For example when converting months or seconds into years.
