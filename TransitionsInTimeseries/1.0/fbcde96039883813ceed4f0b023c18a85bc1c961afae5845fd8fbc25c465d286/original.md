```
significant_transitions(res::ChangesResults, signif::Significance)
```

Estimate significant transtions in `res` using the method described by `signif`. Return `flags`, a Boolean matrix with identical size as the changes stored in `res` (which typically is stored in the field `res.x_change`). `flags` is `true` wherever a change metric of `res` is deemed significant.
