```
prevalence_filter(comm::AbstractAbundanceTable; minabundance=0.0; minprevalence=0.05, renorm=false)
```

Return a filtered `CommunityProfile` where features with prevalence lower than `minprevalence` are removed. By default, a feature is considered "present" if > 0, but this can be changed by setting `minabundance`.

Optionally, set `renorm = true` to calculate relative abundances after low prevalence features are removed.
