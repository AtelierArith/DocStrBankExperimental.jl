```
mannwhitney(data::DataMatrix, column, [group_a, group_b]; var=:copy, obs=:copy, matrix=:keep, kwargs...)
```

2つの観察群間でマン・ホイットニーU検定（ウィルコクソン順位和検定とも呼ばれる）を実行します。U統計量は同点に対して修正され、p値は正規近似を使用して計算されます。

`data`はスパース行列のみを含む`DataMatrix`である必要があります。マン・ホイットニーU検定を実行する前に、生のカウントを最初に[`logtransform`](@ref)（または[`tf_idf_transform`](@ref））することをお勧めします。

`mannwhitney`は`data`のコピーを作成し、`data.var`にU統計量とp値の列を追加します。グループや`kwargs`の詳細については、[`mannwhitney!`](@ref)および[`mannwhitney_table`](@ref)を参照してください。

参照: [`mannwhitney!`](@ref), [`mannwhitney_table`](@ref)
