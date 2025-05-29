```
insolation(t, ϕ; kwargs...)
```

Calculate daily averaged insolation in W/m² at given time and latitude `t, φ`. `φ` is given in **degrees**, and `t` in **days** (real number or date).

Keywords:

```
Ya = DAYS_IN_ORBIT # = 365.26 # days
t_VE = 76.0 # days of vernal equinox
S_0 = 1362.0 # W/m^2
γ=23.44
ϖ=282.95
e=0.017 # eccentricity
```
