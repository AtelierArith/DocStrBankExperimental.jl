```
@match_fail
```

This statement permits early-exit from the value of a @match case. The programmer may write the value as a `begin ... end` and then, within the value, the programmer may write

```
@match_fail
```

to cause the case to terminate as if its pattern had failed. This permits cases to perform some computation before deciding if the rule "*really*" matched.
