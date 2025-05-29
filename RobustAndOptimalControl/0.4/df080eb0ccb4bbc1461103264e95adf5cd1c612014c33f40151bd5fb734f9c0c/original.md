```
Wh = hanus(W)
```

Return `Wh` on Hanus form. `Wh` has twice the number of inputs, where the second half of the inputs are "actual inputs", e.g., potentially saturated. This is used to endow `W` with anti-windup protection. `W` must have an invertable `D` matrix and be minimum phase.

Ref: Sec 9.4.5 of Skogestad, "Multivariable Feedback Control: Analysis and Design"
