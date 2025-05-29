一般的な平方項の緩和

```
x^2 <= y <= (JuMP.upper_bound(x)+JuMP.lower_bound(x))*x - JuMP.upper_bound(x)*JuMP.lower_bound(x)
```
