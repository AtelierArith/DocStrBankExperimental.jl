```
mutable struct Permission <:AbstractPermission
```

権限は、リソースに対して何が実行できるかのみを知っており、誰がアクションを実行できるかは知りません。

```julia
rent_book = Permission(name="books", resources=["ulysses"], actions=["read", "rent"])
// あるいは
rent_book = Permission("books:ulysses:read,rent")
```
