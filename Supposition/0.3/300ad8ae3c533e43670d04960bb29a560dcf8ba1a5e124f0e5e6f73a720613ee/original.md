```
target!(ts::TestState)
```

If `ts` has a target to go towards set, this will try to climb towards that target by adjusting the choice sequence until `ts` shouldn't generate anymore.

If `ts` is currently tracking an error it encountered, it will try to minimize the stacktrace there instead.
