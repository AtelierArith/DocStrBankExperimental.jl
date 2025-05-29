```
SolverTrace(num_steps[, column=CurrentStep(num_steps), columns...;
                        io=stdout, num_printouts=10, progress_meter=true,
                        print_interval, kwargs...])
```

`num_steps` 回の反復に対して [`SolverTrace`](@ref) を構築し、ソルバートレースに表示される `columns` を指定します。ソルバートレースは `io` に出力され、`num_printouts` 行が表示されます。あるいは、`print_interval` を直接指定することもできます。ソルバートレースの下には、`!progress_meter` でない限りプログレスバーが表示されます。`kwargs...` は `ProgressMeter.Progress` に渡されます。
