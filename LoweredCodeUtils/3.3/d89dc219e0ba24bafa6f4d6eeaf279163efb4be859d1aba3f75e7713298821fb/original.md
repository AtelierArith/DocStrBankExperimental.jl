```
methranges = rename_framemethods!([interp::Interpreter=RecursiveInterpreter()], frame::Frame)
```

Rename the gensymmed methods in `frame` to match those that are currently active. The issues are described in https://github.com/JuliaLang/julia/issues/30908. `frame` will be modified in-place as needed.

Returns a vector of `name=>start:stop` pairs specifying the range of lines in `frame` at which method definitions occur. In some cases there may be more than one method with the same name in the `start:stop` range.
