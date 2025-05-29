```
function summarystats(
    chains;
    sections = _default_sections(chains),
    append_chains= true,
    autocov_method::AbstractAutocovMethod = AutocovMethod(),
    maxlag = 250,
    kwargs...
)
```

チェーン内の各パラメータに対して、平均、標準偏差、モンテカルロ標準誤差、バルクおよびテールの有効サンプルサイズ、$\widehat{R}$診断を計算します。

`append_chains=false`を設定すると、各チェーンの要約統計を含むデータフレームのベクトルが返されます。

有効サンプルサイズを推定する際、自己相関は最大`maxlag`ラグまで計算されます。
