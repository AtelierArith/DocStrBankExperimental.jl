```
rolllist(d :: Dice; generator=false)
rolllist(r :: Roll; generator=false)
```

Show all possible rolllist of dice `d` or roll `r`. For `DiceRoll`s this is a list of all dice results. For `CompositeRoll`s and other `Roll`s where its parts are made of `Roll`s.
