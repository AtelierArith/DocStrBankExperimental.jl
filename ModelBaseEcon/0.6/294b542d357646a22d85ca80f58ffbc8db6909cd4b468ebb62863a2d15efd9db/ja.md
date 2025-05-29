```
@variables model name1 name2 ...
@variables model begin
    name1
    name2
    ...
end
```

モデル内の変数の名前を宣言します。

`begin-end` バージョンでは、変数名の前に説明（ドックストリングのようなもの）や `@log`、`@steady`、`@exog` などのフラグを付けることができます。詳細については [`ModelVariable`](@ref) を参照してください。

また、1つ以上の変数の前に `@delete` を付けることで、モデルから変数を削除することもできます。
