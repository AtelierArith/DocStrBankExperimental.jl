```
@__FILEPATH__ -> SystemPath
```

@**FILEPATH** expands to a path with the absolute file path of the file containing the macro. Returns an empty Path if run from a REPL or if evaluated by julia -e <expr>.
