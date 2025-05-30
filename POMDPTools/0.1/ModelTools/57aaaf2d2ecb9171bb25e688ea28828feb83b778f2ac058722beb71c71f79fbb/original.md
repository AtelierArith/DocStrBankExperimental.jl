```
obs_weight(pomdp, s, a, sp, o)
```

Return a weight proportional to the likelihood of receiving observation o from state sp (and a and s if they are present).

This is a useful shortcut for particle filtering so that the observation distribution does not have to be represented.
