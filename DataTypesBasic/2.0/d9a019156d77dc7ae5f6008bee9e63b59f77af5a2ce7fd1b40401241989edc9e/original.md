```
getright(Identity(23)) == 23
getright(Const(:something))  # throws MethodError
```

Extract a value from a "right" `Identity` value. Will result in loud error when used on anything else. Identical to `Base.get` but explicit about the site (and not defined for other things)
