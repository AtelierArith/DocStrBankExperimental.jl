`Scope{T}`

In GATlab, we handle shadowing with a notion of *scope*. Names shadow between scopes. Anything which binds variables introduces a scope, for instance a `@theory` declaration or a context. For example, here is a scope with 3 elements:

```
x = 3
y = "hello"
z = x 
```

Here z is introduced as an alias for x. It is illegal to shadow within a scope. Overloading is not explicitly treated but can be managed by having values which  refer to identifiers earlier / the present scope. See GATs.jl, for example.
