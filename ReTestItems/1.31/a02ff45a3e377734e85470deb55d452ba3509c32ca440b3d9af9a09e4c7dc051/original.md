```
TestSetup(name, code)
```

A module that a `TestItem` can require to be run before that `TestItem` is run. Used for declaring code that multiple `TestItem`s rely on. Should only be created via the `@testsetup` macro.
