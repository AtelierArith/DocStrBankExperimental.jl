```
sonicspeed(T::Real,G::AbstractMole) = sqrt(gasconstant(G)*heatratio(T,G)*T)
```

Speed of sound wave disturbance at isentropic conditions in ideal gas (m⋅s⁻¹ or ft⋅s⁻¹).
