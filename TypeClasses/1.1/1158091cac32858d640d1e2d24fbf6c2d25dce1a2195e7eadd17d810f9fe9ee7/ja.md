```
@syntax_foreach begin
  # ベクトルは @syntax_foreach 内でネストされた for ループのように振る舞います
  a = [1, 2, 3]
  b = [10, 20]
  @pure a + b
end
# [[11, 21], [12, 22], [13, 23]]
```

これは、`foreach` を使用して map*like と flatmap*like の両方を行うモナディック構文のバリアントです。詳細については `Monadic.@monadic` を参照してください。
