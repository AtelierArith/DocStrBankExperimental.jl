```
show_all_reactions(classfilter="", typenamefilter="")
```

List all registered Reactions with `classname` containing (`occursin`) `classfilter` and `typenamefilter` A Reaction is loaded when the module that defines it is imported.

Examples:

  * `PB.show_all_reactions(r"reservoir"i)` case-insensitive match for classname containing "reservoir".
  * `PB.show_all_reactions("", "Reservoir")` all Reactions defined in a module name containing "Reservoir"
