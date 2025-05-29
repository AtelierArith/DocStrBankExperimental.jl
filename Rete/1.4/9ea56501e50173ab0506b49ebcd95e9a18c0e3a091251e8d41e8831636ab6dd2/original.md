```
CanInstallRulesTrait
```

Having this trait gives the root node of a knowledge base the `install` method to facilitate adding rules to the network.

You can add this trait to `YourType` with

```
CanInstallRulesTrait(::Type{<:YourType}) = CanInstallRulesTrait())
```
