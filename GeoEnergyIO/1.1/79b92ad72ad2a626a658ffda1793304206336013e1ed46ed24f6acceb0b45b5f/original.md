```
summary = read_summary(pth)
summary, raw_summary = read_summary(pth, extra_out = true)
```

Read the SUMMARY file from `pth`. The results are given as a Dict.

# Notes

This function requires the `resdata` Python package to be installed, which will be automatically added to your environment if you first install PythonCall and put `using PythonCall` in your script or REPL.

Uses primarily `resdata.summary.Summary`.
