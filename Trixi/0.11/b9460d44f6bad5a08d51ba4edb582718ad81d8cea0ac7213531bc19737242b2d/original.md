```
ControllerThreeLevel(semi, indicator; base_level=1,
                                      med_level=base_level, med_threshold=0.0,
                                      max_level=base_level, max_threshold=1.0)
```

An AMR controller based on three levels (in descending order of precedence):

  * set the target level to `max_level` if `indicator > max_threshold`
  * set the target level to `med_level` if `indicator > med_threshold`; if `med_level < 0`, set the target level to the current level
  * set the target level to `base_level` otherwise
