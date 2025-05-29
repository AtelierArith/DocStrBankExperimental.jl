```
struct PrintLogger <: Logger ;
function PrintLogger(displaylevel)
```

When you use this logger, you will obtain printouts in stdout, no other logging. The `displaylevel` parameter specifies how much should be printed. The higher the value, the more is printed. Zero means no printouts.
