```
flux2mag(flux[, zero_point, ABwave=number]) -> magnitude
```

### 目的

エルグ/(s cm² Å)で表現されたフラックスをマグニチュードに変換します。

### 説明

これは`mag2flux`の逆です。

### 引数

  * `flux`: マグニチュードに変換されるフラックスで、エルグ/(s cm² Å)で表現されています。
  * `zero_point`: マグニチュードのゼロポイントレベル。指定されない場合は21.1（Code et al 1976）がデフォルトとなります。`ABwave`キーワードが指定されている場合は無視されます。
  * `ABwave`（オプションの数値キーワード）：波長（アンストローム単位）。指定された場合、Oke ABマグニチュード（Oke & Gunn 1983, ApJ, 266, 713; http://adsabs.harvard.edu/abs/1983ApJ...266..713O）が返されます。

### 出力

マグニチュード。

`ABwave`キーワードが設定されている場合、マグニチュードは次の式で与えられます。

$$
\text{ABmag} = -2.5\log_{10}(f) - 5\log_{10}(\text{ABwave}) - 2.406
$$

そうでない場合、マグニチュードは次の式で与えられます。

$$
\text{mag} = -2.5\log_{10}(\text{flux}) - \text{zero point}
$$

### 例

```jldoctest
julia> using AstroLib

julia> flux2mag(5.2e-15)
14.609991640913002

julia> flux2mag(5.2e-15, 15)
20.709991640913003

julia> flux2mag(5.2e-15, ABwave=15)
27.423535345634598
```

### 注意事項

この関数のコードはIDL天文学ユーザーライブラリに基づいています。
