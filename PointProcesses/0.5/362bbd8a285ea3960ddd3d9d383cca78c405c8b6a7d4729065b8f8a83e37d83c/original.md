```
ground_intensity(pp, h, t)
```

Compute the ground intensity for a temporal point process `pp` applied to history `h` at time `t`.

The ground intensity quantifies the instantaneous risk of an event with any mark occurring at time `t` after history `h`:

```
λg(t|h) = Σₘ λ(t,m|h)
```
