```
ControllerThreeLevelCombined(semi, indicator_primary, indicator_secondary;
                             base_level=1,
                             med_level=base_level, med_threshold=0.0,
                             max_level=base_level, max_threshold=1.0,
                             max_threshold_secondary=1.0)
```

An AMR controller based on three levels (in descending order of precedence):

  * set the target level to `max_level` if `indicator_primary > max_threshold`
  * set the target level to `med_level` if `indicator_primary > med_threshold`; if `med_level < 0`, set the target level to the current level
  * set the target level to `base_level` otherwise

If `indicator_secondary >= max_threshold_secondary`, set the target level to `max_level`.
