```
irreducible_monomials(precomp ::RepInIntMod, l :: Int, A :: OreAlg)
```

与えられた `precomp` に基づいて定義されたモジュールの順序に関して、A の順序に対してより小さい代表を持たない、次数 l までのすべてのモノミアルを返します。

警告: precomp のために選択されたパラメータ sigma が十分に大きくない場合、この関数は一部の可約モノミアルを返す可能性があります。
