```
filepath, line = whereis(lineinfo, method::Method)
```

Return the file and line number associated with a specific statement in `method`. `lineinfo.line` should contain the line number of the statement at the time `method` was compiled. The current location is returned.
