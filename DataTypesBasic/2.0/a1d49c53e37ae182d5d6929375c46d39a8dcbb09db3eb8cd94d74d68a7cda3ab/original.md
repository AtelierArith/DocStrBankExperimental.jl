```
getrightOption(Identity(23)) == Option(23)
getrightOption(Const(:something)) == Option()
```

Convert to option, assuming you want to have the right value be preserved. Identical to `getOption`, just explicit about the site.
