```
assume_role(role; kwargs...) -> Function
```

Create a function that assumes the IAM `role` via a deferred principal entity, i.e. a function equivalent to `principal -> assume_role(principal, role; kwargs...)`. Useful for [role chaining](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-role-chaining).

# Examples

Assume "role-a" which in turn assumes "role-b":

```julia
AWSConfig() |> assume_role("role-a") |> assume_role("role-b")
```
