```
mtxexpsplot(ps_data,dt=0.1,nmax=50; gs::GUIState = defaultgs(), gradual=false)
```

plot the evolution of `∥e^(tA)∥`.

This is useful for analyzing linear initial value problems `∂x/∂t = Ax`.
