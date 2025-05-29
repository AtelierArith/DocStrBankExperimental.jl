```
@match_return value
```

This statement permits early-exit from the value of a @match case. The programmer may write the value as a `begin ... end` and then, within the value, the programmer may write

```
@match_return value
```

to terminate the value expression **early** with success, with the given value.
