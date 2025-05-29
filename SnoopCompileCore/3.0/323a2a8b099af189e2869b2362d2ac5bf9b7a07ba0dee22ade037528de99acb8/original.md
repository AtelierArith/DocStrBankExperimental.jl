```
@snoop_llvm "func_names.csv" "llvm_timings.yaml" begin
    # Commands to execute, in a new process
end
```

causes the julia compiler to log timing information for LLVM optimization during the provided commands to the files "func*names.csv" and "llvm*timings.yaml". These files can be used for the input to `SnoopCompile.read_snoop_llvm("func_names.csv", "llvm_timings.yaml")`.

The logs contain the amount of time spent optimizing each "llvm module", and information about each module, where a module is a collection of functions being optimized together.
