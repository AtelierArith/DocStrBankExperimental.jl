```
@⌛ [label] code ...
@⌛ [label] function_definition() = ....
```

Label a section of code to be timed. If a label string is not provided, the first form uses the code itselfs as a label, the second uses the function name, and its the body of the function which is timed. 

To run the timer and print output, returning the result of the calculation, use

```
@show⌛ run_code()
```

Timing uses `TimerOutputs.get_defaulttimer()`. 
