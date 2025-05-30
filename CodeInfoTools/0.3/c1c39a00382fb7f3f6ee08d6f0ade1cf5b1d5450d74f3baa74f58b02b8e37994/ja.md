```
finish(b::Builder)
```

[`Builder`](@ref)から新しい`CodeInfo`インスタンスを作成します。ラップされた[`Canvas`](@ref)をインプレースで再番号付けし、その後、元の`CodeInfo`インスタンスから情報をコピーし、ラップされた[`Canvas`](@ref)からの変更を挿入します。
