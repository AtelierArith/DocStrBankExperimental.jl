```
getleftOption(Identity(23)) == Option()
getleftOption(Const(:something)) == Option(:something)
```

Convert to option, assuming you want to have the left value be preserved.
