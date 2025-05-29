```
@autoexogenize model begin
    varname = shkname
    ...
end
```

変数とショックの間のマッピングを定義して、外生変数と内生変数を便利に入れ替えることができます。

削除するペアの前に `@delete` を付けることで、モデルからペアを削除することもできます。
