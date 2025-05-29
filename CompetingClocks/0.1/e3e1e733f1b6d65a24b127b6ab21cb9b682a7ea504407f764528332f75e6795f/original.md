```
FirstReaction{KeyType,TimeType}()
```

This is the classic first reaction method for general distributions.  Every time you sample, this goes to each distribution and asks when it would fire. Then it takes the soonest and throws out the rest of the sampled times until the next sample. It can also be very fast when there are only a few clocks to sample.

One interesting property of this sampler is that you can call `next()` multiple times in order to get a distribution of next firing clocks and their times to fire.
