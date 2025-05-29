general relaxation of a square term

```
x^2 <= y <= (JuMP.upper_bound(x)+JuMP.lower_bound(x))*x - JuMP.upper_bound(x)*JuMP.lower_bound(x)
```
