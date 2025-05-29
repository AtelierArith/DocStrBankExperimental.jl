```
format_A_X(default_metals_H, default_alpha_H, abundances; kwargs... )
```

水素からウランまでの元素の$A(X)$ ($\log_{10}(X/H) + 12$)形式の豊富さを含む92要素のベクトルを返します。

# 引数

これらの位置引数で豊富さを指定できます。すべてオプションですが、`default_alpha_H`が提供されている場合、`default_metals_H`も提供されている必要があります。

  * `default_metals_H` (デフォルト: 0)、すなわち[metals/H]は、Heより重い元素の$\log_{10}$太陽相対豊富さです。これは、要素ごとに`default_alpha`および`abundances`によって上書きされます。
  * `default_alpha_H` (デフォルト: `default_metals_H`と同じ)、すなわち[alpha/H]は、アルファ元素の$\log_{10}$太陽相対豊富さです（下記の`alpha_elements`を参照）。これは、要素ごとに`abundances`によって上書きされます。
  * `abundances`は、原子番号または記号を[$X$/H]豊富さにマッピングする`Dict`です。（$A(X)$豊富さを使用するには`solar_relative=false`を設定します。）これらは`default_metals_H`を上書きします。これは、非太陽のHeの豊富さを指定する唯一の方法です。

# キーワード引数

  * `solar_relative` (デフォルト: true): trueの場合、豊富さを[$X$/H]($\log_{10}$太陽相対)形式として解釈します。falseの場合、$A(X)$豊富さ、すなわち$A(x) = \log_{10}(n_X/n_\mathrm{H}) + 12$として解釈します。ここで、$n_X$は$X$の数密度です。指定されていない豊富さはデフォルトで太陽値に依存し、`default_metals_H`および`default_alpha_H`に従って設定されます。
  * `solar_abundances` (デフォルト: `Korg.asplund_2020_solar_abundances`)は、原子番号でインデックス付けされた太陽豊富さのセットです。`Korg.asplund_2009_solar_abundances`および`Korg.grevesse_2007_solar_abundances`も便利のために提供されています。
  * `alpha_elements` (デフォルト: [`Korg.default_alpha_elements`](@ref)): アルファ元素の原子番号のベクトルです。（慣習が異なるため便利です。）
