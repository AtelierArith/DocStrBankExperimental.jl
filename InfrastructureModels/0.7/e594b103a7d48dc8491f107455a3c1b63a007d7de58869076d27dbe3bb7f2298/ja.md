三次元項の凸包緩和

```
w₁ = JuMP.lower_bound(x)*JuMP.lower_bound(y)*JuMP.lower_bound(z)
w₂ = JuMP.lower_bound(x)*JuMP.lower_bound(y)*JuMP.upper_bound(z)
w₃ = JuMP.lower_bound(x)*JuMP.upper_bound(y)*JuMP.lower_bound(z)
w₄ = JuMP.lower_bound(x)*JuMP.upper_bound(y)*JuMP.upper_bound(z)
w₅ = JuMP.upper_bound(x)*JuMP.lower_bound(y)*JuMP.lower_bound(z)
w₆ = JuMP.upper_bound(x)*JuMP.lower_bound(y)*JuMP.upper_bound(z)
w₇ = JuMP.upper_bound(x)*JuMP.upper_bound(y)*JuMP.lower_bound(z)
w₈ = JuMP.upper_bound(x)*JuMP.upper_bound(y)*JuMP.upper_bound(z)
w = λ₁*w₁ + λ₂*w₂ + λ₃*w₃ + λ₄*w₄ + λ₅*w₅ + λ₆*w₆ + λ₇*w₇ + λ₈*w₈
x = (λ₁ + λ₂ + λ₃ + λ₄)*JuMP.lower_bound(x) + (λ₅ + λ₆ + λ₇ + λ₈)*JuMP.upper_bound(x)
y = (λ₁ + λ₂ + λ₅ + λ₆)*JuMP.lower_bound(y) + (λ₃ + λ₄ + λ₇ + λ₈)*JuMP.upper_bound(y)
z = (λ₁ + λ₃ + λ₅ + λ₇)*JuMP.lower_bound(z) + (λ₂ + λ₄ + λ₆ + λ₈)*JuMP.upper_bound(z)
λ₁ + λ₂ + λ₃ + λ₄ + λ₅ + λ₆ + λ₇ + λ₈ = 1
```
