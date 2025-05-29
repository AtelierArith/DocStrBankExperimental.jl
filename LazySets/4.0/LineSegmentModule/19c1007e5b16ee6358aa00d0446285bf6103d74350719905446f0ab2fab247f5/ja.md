# 拡張ヘルプ

```
intersection(LS1::LineSegment, LS2::LineSegment)
```

### 出力

`Singleton`、`LineSegment`、または交差の結果に応じて`EmptySet`。

### 注意事項

  * 線分が交差する場合、または平行で単一の共通点がある場合、その点が返されます。
  * 線分が平行で共通の線分がある場合、その線分が返されます。
  * それ以外の場合、交差はなく、空集合が返されます。
