```
ret = methoddef!([interp::Interpreter=RecursiveInterpreter()], signatures, frame; define=true)
```

Compute the signature of a method definition. `frame.pc` should point to a `:method` expression. Upon exit, the new signature will be added to `signatures`.

There are several possible return values:

```
pc, pc3 = ret
```

is the typical return. `pc` will point to the next statement to be executed, or be `nothing` if there are no further statements in `frame`. `pc3` will point to the 3-argument `:method` expression.

Alternatively,

```
pc = ret
```

occurs for "empty method" expressions, e.g., `:(function foo end)`. `pc` will be `nothing`.

By default the method will be defined (evaluated). You can prevent this by setting `define=false`. This is recommended if you are simply extracting signatures from code that has already been evaluated.
