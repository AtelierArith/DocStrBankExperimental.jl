```
fig = mvnyquistplot(sys, w;  unit_circle=true, hz = false, kwargs...)
```

Create a Nyquist plot of the `LTISystem`. A frequency vector `w` must be provided.

  * `unit_circle`: if the unit circle should be displayed

If `hz=true`, the hover information will be displayed in Hertz, the input frequency vector is still treated as rad/s.

`kwargs` is sent as argument to plot.

# Example

```julia
w = 2π .* exp10.(LinRange(-2, 2, 500))
W = makeweight(0.40, 15, 3) # frequency weight for uncertain dynamics
Pn = tf(1, [1/60, 1]) |> ss # nominal plant
d = δss(1,1)                # Uncertain dynamics

Pd = Pn*(I(1) + W*d)        # weighted dynamic uncertainty on the input of Pn
Pp = rand(Pd, 200)          # sample the uncertain plant
Gcl = lft(Pd, ss(-1))       # closed loop system
structured_singular_value(Gcl) # larger than 1 => not robustly stable
unsafe_comparisons(true)
mvnyquistplot(Pp, w, points=true) # MV Nyquist plot encircles origin for some samples => not robustly stable
```
