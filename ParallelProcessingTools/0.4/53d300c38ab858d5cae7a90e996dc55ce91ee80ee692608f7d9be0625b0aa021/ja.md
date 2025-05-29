```
abstract type WriteMode
```

書き込みモードのための抽象型。

次のサブタイプのいずれかである可能性があります: [`CreateNew`](@ref), [`CreateOrIgnore`](@ref), [`CreateOrReplace`](@ref), [`CreateOrModify`](@ref), [`ModifyExisting`](@ref)。

[`write_files`](@ref)によって使用されます。
