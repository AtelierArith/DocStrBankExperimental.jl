```
getOption(Identity(23)) == Option(23)
getOption(Const(:something)) == Option()
```

Convert to option, assuming you want to have the right value be preserved, and the left value represented as `Option()`.
