```
update(las::LAS, [attributes]; kws...)
```

`LAS`のコピーを作成し、提供された`NamedTuple`としての`attributes`でポイント属性を置き換えます。キーワード引数は、[`LAS`](@ref)の対応するグローバル属性を更新します。

関連情報: [`update!`](@ref)
