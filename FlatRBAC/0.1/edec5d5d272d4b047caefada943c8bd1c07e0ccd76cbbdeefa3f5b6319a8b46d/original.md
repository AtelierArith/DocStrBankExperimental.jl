```
mutable struct Permission <:AbstractPermission
```

Permissions dot not know `who` can perform actions, only what can be performed on resources

```julia
rent_book = Permission(name="books", resources=["ulysses"], actions=["read", "rent"])
// alternatively
rent_book = Permission("books:ulysses:read,rent")
```
