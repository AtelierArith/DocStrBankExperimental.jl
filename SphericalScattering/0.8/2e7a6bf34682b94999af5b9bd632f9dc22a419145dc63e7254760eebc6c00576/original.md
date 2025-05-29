```
DielectricSphereThinImpedanceLayer(
    radius    = error("missing argument `radius`"),
    thickness = error("missing argument `thickness` of the coating"),
    thinlayer = error("missing argument `thinlayer`"),
    filling   = error("missing argument `filling`")
)
```

Constructor for the dielectric sphere with a thin impedance layer. For this model, it is assumed that the displacement field is only radial direction in the layer, which requires a small thickness and low conductivity. For details, see for example T. B. Jones, Ed., “Models for layered spherical particles,” in Electromechanics of Particles, Cambridge: Cambridge University Press, 1995,  pp. 227–235. doi: 10.1017/CBO9780511574498.012.
