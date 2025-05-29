```
mag2flux(mag[, zero_point, ABwave=number]) -> flux
```

### 目的

明るさからフラックスに変換します。フラックスはerg/(s cm² Å)で表されます。

### 説明

これは`flux2mag`の逆です。

### 引数

  * `mag`: フラックスに変換される明るさ。
  * `zero_point`: 明るさのゼロポイントレベル。指定しない場合は21.1（Code et al 1976）がデフォルトです。`ABwave`キーワードが指定されている場合は無視されます。
  * `ABwave`（オプションの数値キーワード）：波長（アンストローム単位）。指定された場合、入力の`mag`はOke AB明るさ（Oke & Gunn 1983, ApJ, 266, 713; http://adsabs.harvard.edu/abs/1983ApJ...266..713O）を含むと仮定されます。

### 出力

フラックス。

`ABwave`キーワードが設定されている場合、フラックスは次の式で与えられます。

$$
\text{flux} = 10^{-0.4(\text{mag} +2.406 + 4\log_{10}(\text{ABwave}))}
$$

そうでない場合、フラックスは次のように与えられます。

$$
\text{flux} =  10^{-0.4(\text{mag} + \text{zero point})}
$$

### 例

```jldoctest
julia> using AstroLib

julia> mag2flux(8.3)
1.7378008287493692e-12

julia> mag2flux(8.3, 12)
7.58577575029182e-9

julia> mag2flux(8.3, ABwave=12)
3.624411568301719e-7
```

### 注意事項

この関数のコードはIDL天文学ユーザーライブラリに基づいています。
