```
@alias name
```

パラメータエイリアスを作成します。モデル定義の[`@parameters`](@ref)セクションで`@alias`を使用します。

```
@parameters model begin
    a = 5
    b = @alias a
end
```
