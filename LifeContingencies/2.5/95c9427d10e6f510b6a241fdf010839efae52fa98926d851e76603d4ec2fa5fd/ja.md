```
omega(lc::LifeContingency)
omega(l::Life)
omega(i::InterestRate)
```

# `Life`s と `LifeContingency`s

利率と死亡率表の両方に対して最後に定義された時間*期間を返します。これは、`MortalityTable` に対して `omega` を呼び出すこととは *異なる* ことに注意してください。後者は最後の `attained*age` を返します。

例: `LifeContingency` の発行年齢が 60 で、`MortalityTable` の最後に定義された到達年齢が 100 の場合、`MortalityTable` の `omega` は `100` になり、`LifeContingency` の `omega` は `40` になります。

# `InterestRate`s

利率が定義されている最後の期間です。機能的および定常利率タイプの場合、無限大（`Inf`）であると仮定されます。ベクトルタイプの場合は、ベクトルの `lastindex` を返します。
