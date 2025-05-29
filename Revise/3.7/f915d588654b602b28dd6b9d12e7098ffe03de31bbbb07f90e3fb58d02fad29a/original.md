```
entr(f, files; all=false, postpone=false, pause=0.02)
entr(f, files, modules; all=false, postpone=false, pause=0.02)
```

Execute `f()` whenever files or directories listed in `files`, or code in `modules`, updates. If `all` is `true`, also execute `f()` as soon as code updates are detected in any module tracked by Revise.

`entr` will process updates (and block your command line) until you press Ctrl-C. Unless `postpone` is `true`, `f()` will be executed also when calling `entr`, regardless of file changes. The `pause` is the period (in seconds) that `entr` will wait between being triggered and actually calling `f()`, to handle clusters of modifications, such as those produced by saving files in certain text editors.

# Example

```julia
entr(["/tmp/watched.txt"], [Pkg1, Pkg2]) do
    println("update")
end
```

This will print "update" every time `"/tmp/watched.txt"` or any of the code defining `Pkg1` or `Pkg2` gets updated.
