```
SecretBlock(blockname::String, blocktype::String, value::SecretString) <: AbstractPrefectBlock
```

A struct for storing a Prefect Block with a SecretString as value field. This permits retrieving secrets from the Prefect Server/Prefect Cloud. The secret field is accessible via the `value.secret` field.

*NOTE:* This is not an ecrypted secrets store, it is a log obfuscator.

# Example:

```jldoctest
julia> using PrefectInterfaces

julia> secretblock = SecretBlock("secret", "necromancer", "abcd1234")
SecretBlock("secret", "necromancer", ####Secret####)

julia> dump(secretblock, maxdepth = 10)
SecretBlock
  blockname: String "secret"
  blocktype: String "necromancer"
  value: SecretString

julia> secretblock.value.secret
"abcd1234"
```
