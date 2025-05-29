```
Permission(str::String, description::String="")
```

Build a Permission from a shorthand representation

# Examples

```julia
Permission("client:books:read,rent")
# Permission("client", ["books"], ["read", "rent"], "", None)

Permission("client::read,rent") # any resource
# Permission("client", ["*"], ["read", "rent"], "", None)

Permission("admin") # any resource, any actions
# Permission("admin", ["*"], ["*"], "", None)

Permission("staff:books") # any action over books
# Permission(staff:books:*:none)

Permission("multi-rental:books,cds:rent")
# Permission("multi-rental", ["books", "cds"], ["rent"], "", None)

Permission("author:*:update:own", "An author can update their own resources")
# Permission("author", ["*"], ["update"], "An author can update their own resources", Own)
```
