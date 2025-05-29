```
mutable struct Subject <:AbstractSubject
```

A subject represents and entity interacting with an application

In a flat RBAC model, subjects will obtain permissions from their assigned roles, direct assignment is not supported

# Methods

  * grant!
  * revoke!
