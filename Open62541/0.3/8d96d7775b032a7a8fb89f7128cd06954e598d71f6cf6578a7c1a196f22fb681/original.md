```
JUA_UsernamePasswordLogin 
```

creates a `JUA_UsernamePasswordLogin` object - the equivalent of a `UA_UsernamePasswordLogin` object, but with memory managed by Julia rather than C.

The following methods are defined:

```
JUA_UsernamePasswordLogin(username::AbstractString, password::AbstractString)
```

Example:

```
j = JUA_UsernamePasswordLogin("PeterParker", "IamSpiderman")

```
