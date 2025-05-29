```
SecretString(secret::String) <:Any
```

A struct for storing secret values with overrides of `show` and `dump` to prevent its field from being exposed in plaintext in logs. The secret field is accessible via the `secret` field.

*NOTE:* This is not an ecrypted secrets store, it is a log obfuscator.

# Example:

```jldoctest
julia> using PrefectInterfaces

julia> password = SecretString("abcd1234")
####Secret####

julia> show(password)
####Secret####
julia> password.secret
"abcd1234"
```
