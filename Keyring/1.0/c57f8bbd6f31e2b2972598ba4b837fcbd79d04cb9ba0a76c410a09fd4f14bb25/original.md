```
get_credential(target::AbstractString)
get_credential(store::AbstractCredentialStore, target::AbstractString)
```

Returns either a [Credential](@ref) or `Some(nothing)` if the credential is not found.

If not given, `store` defaults to the value of [`DEFAULT_CREDENTIAL_STORE`](@ref).

# Examples

```julia_repl
julia> set_credential("my_target", "my_username", "my_secret")
julia> c = get_credential("my_target")
```
