```
BraidingStyle(::Sector) -> ::BraidingStyle
BraidingStyle(I::Type{<:Sector}) -> ::BraidingStyle
```

タイプ `I` のセクターのブレーディングとツイストの挙動を返します。これは次のいずれかです。

  * `Bosonic()`: 自明なツイストを持つ対称的なブレーディング（すなわち、恒等）
  * `Fermionic()`: 非自明なツイストを持つ対称的なブレーディング（恒等に平方する）
  * `Anyonic()`: 一般的な $R_(a,b)^c$ フェーズまたは行列（`SimpleFusion` または `GenericFusion` 融合に依存）および任意のツイスト

`Bosonic` と `Fermionic` は `SymmetricBraiding` のサブタイプであることに注意してください。これは、ブレードが実際には交差に等しいことを意味します（すなわち、2回ブレーディングすることは恒等です：`isone(Rsymbol(b,a,c)*Rsymbol(a,b,c)) == true`）および置換は一意に定義されます。
