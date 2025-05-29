```
init_m0_skyrmion(sim::AbstractSim, center::Tuple, R::Float64; ratio=0.7, p=-1, c=1, type="B")
```

Set the magnetization with skyrmions. Note that this function can be called mulitple times to add more skyrmons.

center :  the skyrmion center, should be a Tuple. For example, center = (50e-9,50e-9)

R : the skyrmion radius.

ratio : ratio=w/R where w is the width of domain wall. By default ratio = 0.7

p : polarity, +1 –> core up; -1 –> core down

c : chirality, +1 –> lefthand,for positive D; -1 –> righthand,for negative D

type : "B" or "N", representing Bloch or Neel skyrmions.

For example:

```julia
    init_m0_skyrmion(sim, (50e-9,50e-9), 2e-8, ratio=0.5, p=-1, c=1, type="B")
```
