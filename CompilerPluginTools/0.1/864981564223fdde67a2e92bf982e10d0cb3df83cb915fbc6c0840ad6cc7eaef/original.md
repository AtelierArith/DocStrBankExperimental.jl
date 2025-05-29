```
code_ircode([pass, ]f, types; world=get_world_counter(), interp=NativeInterpreter(world))
```

Get `IRCode` by given function `f` and its argument types `types`. An option argument `pass` can be specified as a transform function on IRCode during type inference.
