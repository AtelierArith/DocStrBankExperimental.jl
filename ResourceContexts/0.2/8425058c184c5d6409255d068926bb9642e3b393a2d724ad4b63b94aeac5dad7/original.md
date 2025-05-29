```
@context begin ... end
@context function f() ... end
```

`@context` creates a local context and runs the provided code within that context. When the code exits, any resources registered with the context will be cleaned up with `ResourceContexts.cleanup!()`.

When the code is a `function` definition, the context block is inserted around the function body.
