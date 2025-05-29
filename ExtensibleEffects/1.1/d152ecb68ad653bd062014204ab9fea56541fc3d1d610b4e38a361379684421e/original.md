```
@syntax_eff_noautorun begin
  a = [1,2,3]
  b = [a, a*a]
  @pure a, b
end
```

Extensible Effects syntax which does not run `autorun` routine. As `@syntax_eff`, it applies `effect` to all values which are not prefaced with `@pure`,  which lifts them into the `Eff` monad. The results are combined using `@syntax_flatmap` on the respective `Eff` monad, which then is directly returned.

## Examples

```julia
unhandled_eff = @syntax_eff_noautorun begin
  a = [1,2,3]
  b = [a, a*a]
  @pure a, b
end

mycustomwrapper(i::Int) = collect(1:i)
# monadic-like syntax to first apply a wrapper before interpreting code to unhandled effects
unhandled_eff = @syntax_eff_noautorun mycustomwrapper begin
  a = [1,2,3]
  b = [a, a*a]
  @pure a, b
end
```
