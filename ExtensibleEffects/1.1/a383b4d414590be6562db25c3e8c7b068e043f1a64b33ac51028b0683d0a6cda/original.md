```
@runhandlers handlers eff
```

For convenience we provide `runhandlers` function also as a macro.

With this you can easier run left-over handlers from an `@syntax_eff` autorun.

## Example

```
@runhandlers WithCall(args, kwargs) @syntax_eff begin
  a = Callable(x -> 2x)
  @pure a
end
```
