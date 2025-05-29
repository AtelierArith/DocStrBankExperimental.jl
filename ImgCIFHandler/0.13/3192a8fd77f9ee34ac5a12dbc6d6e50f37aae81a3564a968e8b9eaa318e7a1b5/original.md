```
peak_to_frames(p::Peak, cc::CifContainer;single=false, friedel=true)
```

Given peak `p`, return an array of peaks that the pixel should appear, if at all. If only peaks from the same scan should be checked, `single` should be true.
