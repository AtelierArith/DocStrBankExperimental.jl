```
@syntax_flatmap begin
  # ベクターは @syntax_flatmap 内のネストされた for ループに似た動作をします
  a = [1, 2, 3]
  b = [10, 20]
  @pure a + b
end
# [11, 21, 12, 22, 13, 23]
```

これは、`map` を map*like に、`flatmap` を flatmap*like に使用する標準的なモナディック構文です。詳細については `Monadic.@monadic` を参照してください。
