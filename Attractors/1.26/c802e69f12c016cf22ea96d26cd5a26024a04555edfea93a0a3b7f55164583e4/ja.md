```
IDMatcher
```

すべての「マッチャー」のスーパークラスであり、アトラクタをラベル付けするIDに一致します。現在利用可能なマッチャー：

  * [`MatchBySSSetDistance`](@ref)
  * [`MatchByBasinEnclosure`](@ref)
  * [`MatchByBasinOverlap`](@ref)

マッチャーは、関数[`matching_map`](@ref)に基づいた拡張可能なインターフェースを実装しています。この関数は、グローバル継続への呼び出しの後に、アトラクタを異なる方法でマッチさせるために呼び出すことができる高レベル関数[`match_sequentially!`](@ref)によって使用されます。継続中に元々使用されたマッチングが最適でなかった場合に使用されます。
