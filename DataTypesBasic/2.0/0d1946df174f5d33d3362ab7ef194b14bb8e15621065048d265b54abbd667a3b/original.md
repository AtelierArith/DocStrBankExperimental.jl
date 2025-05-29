```
getleft(Const(:something)) == :something
getleft(Identity(23))  # throws MethodError
```

Extract a value from a "left" `Const` value. Will result in loud error when used on anything else.
