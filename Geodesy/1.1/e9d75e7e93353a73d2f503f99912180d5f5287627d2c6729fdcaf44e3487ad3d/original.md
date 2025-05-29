```
UTMfromENU(origin, zone, isnorth, datum)
```

Creates composite transformation `UTMfromLLA(zone, isnorth, datum) ∘ LLAfromENU(origin, datum)`. If `origin` is a `UTM` point, then it is assumed it is in the given specified zone and hemisphere.
