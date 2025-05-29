with_repr(typedef::Expr)

マクロ @with_repr のための関数で、型のための `Base.show` メソッドを作成します。

`show` メソッドは、型のフィールド名/型とフィールドの値を表示します。

# 例

```
@with_repr struct TestStruct2
x::Int
name::String
y
end
```
