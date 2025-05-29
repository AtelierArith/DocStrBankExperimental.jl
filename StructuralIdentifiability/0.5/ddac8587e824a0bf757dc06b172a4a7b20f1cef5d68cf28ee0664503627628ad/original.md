```
find_submodels(ode)
```

The function calculates and returns all valid submodels given a system of ODEs.

Input:

  * `ode` - an ODEs system to be studied

Output: 

  * A list of submodels represented as `ode` objects

Example:

```
>ode = @ODEmodel(x1'(t) = x1(t)^2, 
                 x2'(t) = x1(t) * x2(t), 
                 y1(t) = x1(t), 
                 y2(t) = x2(t))
>find_submodels(ode)
    ODE{QQMPolyRingElem}[
        
        x1'(t) = a(t)*x2(t)^2 + x1(t)
        y1(t) = x1(t)
    ]
```
