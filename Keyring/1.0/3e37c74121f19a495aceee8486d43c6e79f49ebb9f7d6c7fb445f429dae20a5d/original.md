```
set_credential(target::AbstractString, username::AbstractString, secret::AbstractString)
set_credential(store::AbstractCredentialStore, target::AbstractString, username::AbstractString, secret::AbstractString)
```

Sets the value and returns `nothing`.

If not given, `store` defaults to the value of [`DEFAULT_CREDENTIAL_STORE`](@ref).
