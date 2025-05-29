```
SecretString(secret::String) <:Any
```

平文でログにフィールドが露出するのを防ぐために、`show` と `dump` をオーバーライドした秘密値を格納するための構造体です。秘密フィールドは `secret` フィールドを介してアクセス可能です。

*注意:* これは暗号化された秘密ストアではなく、ログの難読化ツールです。

# 例:

```jldoctest
julia> using PrefectInterfaces

julia> password = SecretString("abcd1234")
####Secret####

julia> show(password)
####Secret####
julia> password.secret
"abcd1234"
```
