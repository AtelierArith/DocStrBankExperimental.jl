```
enum_matcher(Enum, value)::Expr
```

`value`が`Enum`のケースであるかどうかをテストするために使用される式を生成します。

これは`is_enum(Enum)`が`true`のときのみ機能することに注意してください!!!

```
@match V begin
    Enum => ...
@end
```

上記の単一ケースは次の条件で一致します。

1. `enum_matcher(Enum, ::Any)`が定義されておらず、`V == Enum`である。
2. `enum_matcher(Enum, :V)`から生成された式が現在のモジュールで`true`に評価される。
