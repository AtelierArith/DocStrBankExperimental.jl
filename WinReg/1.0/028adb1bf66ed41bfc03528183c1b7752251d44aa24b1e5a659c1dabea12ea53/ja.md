```
openkey(basekey::RegKey, path::AbstractString, accessmask::UInt32=KEY_READ)
```

`basekey`に対して相対的な`path`でレジストリキーを開きます。`accessmask`はビットフィールドです。`\`はパスセパレータとして使用されます。
