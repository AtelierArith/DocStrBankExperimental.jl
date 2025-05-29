```
SecretBlock(blockname::String, blocktype::String, value::SecretString) <: AbstractPrefectBlock
```

SecretStringを値フィールドとして持つPrefect Blockを格納するための構造体です。これにより、Prefect Server/Prefect Cloudから秘密を取得することができます。秘密フィールドには`value.secret`フィールドを介してアクセスできます。

*注意:* これは暗号化された秘密ストアではなく、ログの難読化ツールです。

# 例:

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
