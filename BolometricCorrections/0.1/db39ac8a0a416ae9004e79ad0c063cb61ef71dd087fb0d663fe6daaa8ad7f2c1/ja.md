```
X(mix::AbstractChemicalMixture, Z)
```

与えられた原始星の金属質量 `Z` と提供された化学混合物に基づいて、**原始星**水素質量比を返します。一般的なメソッドは `1 - Y(mix, Z) - Z` を返します。
