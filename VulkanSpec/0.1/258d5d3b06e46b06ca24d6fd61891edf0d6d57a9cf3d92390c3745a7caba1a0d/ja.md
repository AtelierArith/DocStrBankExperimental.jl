```
len(pCode)
```

提供されたポインタ引数の長さを説明する関数パラメータまたは構造体メンバーを返します。長さが単純な引数よりも複雑な場合、すなわち他のパラメータの関数である場合、`missing`が返されます。この場合、正しい`Expr`を取得するには、引数の`.len`フィールドを参照してください。
