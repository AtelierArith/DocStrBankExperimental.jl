```
BerendsenBarostat(pressure, coupling_const; compressibility=4.6e-5u"bar^-1",
                  max_scale_frac=0.1, n_steps=1)
```

The Berendsen barostat for controlling pressure.

The scaling factor for the box every `n_steps` steps is

$$
\mu = 1 - \frac{\kappa_T \delta t}{3 \tau} ( P_0 - P )
$$

with the fractional change limited to `max_scale_frac`.

This barostat should be used with caution as it can lead to simulation artifacts.
