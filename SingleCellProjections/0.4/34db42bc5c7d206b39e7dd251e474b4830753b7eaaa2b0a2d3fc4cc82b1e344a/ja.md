```
mannwhitney!(data::DataMatrix, column, [group_a, group_b]; kwargs...)
```

2つの観察群間でマン・ホイットニーU検定（ウィルコクソン順位和検定とも呼ばれる）を実行します。U統計量はタイに対して修正され、p値は正規近似を使用して計算されます。

`data`はスパース行列のみを含む`DataMatrix`である必要があります。マン・ホイットニーU検定を実行する前に、生のカウントをまず[`logtransform`](@ref)（または[`tf_idf_transform`](@ref））することをお勧めします。

`mannwhitney!`は`data.var`にU統計量とp値の列を追加します。グループとkwargsの詳細については、[`mannwhitney_table`](@ref)を参照してください。

さらに、`mannwhitney!`は次の`kwarg`をサポートしています：

  * `prefix` - U統計量とp値の出力列名は、この文字列で接頭辞が付けられます。指定がない場合は、`column`、`group_a`、`group_b`から構築されます。

参照：[`mannwhitney_table`](@ref)、[`mannwhitney`](@ref)
