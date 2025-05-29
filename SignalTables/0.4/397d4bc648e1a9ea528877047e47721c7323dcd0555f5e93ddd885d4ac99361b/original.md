```
writeSignalTable(filename::String, signalTable; signalNames=nothing, indent=nothing, log=false)
```

Write signalTable in JSON format on file `filename`.

If keyword signalNames with a Vector of strings is provided, then a signal table with the corresponding signals are stored on file.

If indent=<number> is given, then <number> indentation is used (otherwise, compact representation)
