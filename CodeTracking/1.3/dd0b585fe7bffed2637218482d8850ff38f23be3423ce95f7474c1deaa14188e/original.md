```
filepath, line = whereis(method::Method)
```

Return the file and line of the definition of `method`. The meaning of `line` depends on the Julia version: on Julia 1.5 and higher it is the line number of the method declaration, otherwise it is the first line of the method's body.
