```
refresh_rules()
refresh_rules(frule | rrule)
```

This triggers all [`on_new_rule`](@ref) hooks to run on any newly defined rules. It is *automatically* run when ever a package is loaded. It can also be manually called to run it directly, for example if a rule was defined in the REPL or within the same file as the AD function.
