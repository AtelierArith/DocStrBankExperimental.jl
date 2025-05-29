```
mannwhitney_table(data::DataMatrix, column, [group_a, group_b]; kwargs...)
```

2つの観察グループ間でマン・ホイットニーU検定（ウィルコクソン順位和検定とも呼ばれる）を実行します。U統計量はタイに対して補正され、p値は正規近似を使用して計算されます。

`data`はスパース行列のみを含む`DataMatrix`である必要があります。マン・ホイットニーU検定を実行する前に、生のカウントを最初に[`logtransform`](@ref)（または[`tf_idf_transform`](@ref））することをお勧めします。

`column`は`data.obs`内の列を指定し、どの観察がどのグループに属するかを決定するために使用されます。

`group_a`と`group_b`が指定されていない場合、`column`には正確に2つのユニークな値（`missing`を除く）が含まれている必要があります。`group_a`が指定されているが`group_b`が指定されていない場合、グループAの観察は他のすべての観察（`missing`を除く）と比較されます。両方の`group_a`と`group_b`が指定されている場合、グループAの観察はグループBの観察と比較されます。

`mannwhitney_table`は、変数ID、U統計量、およびp値の列を持つDataFrameを返します。

サポートされている`kwargs`は次のとおりです：

  * `statistic_col="U"`   - U統計量を含む出力列の名前。（出力から削除するには何も設定しないでください。）
  * `pvalue_col="pValue"` - p値を含む出力列の名前。（出力から削除するには何も設定しないでください。）
  * `h1_missing=:skip`    - `:skip`または`:error`のいずれか。`skip`の場合、`column`内の欠損値はスキップされ、それ以外の場合はエラーが発生します。

次の`kwargs`は、計算がどのようにスレッド化されるかを決定します：

  * `nworkers`      - 計算に使用されるワーカースレッドの数。スレッドを無効にするには1に設定します。
  * `chunk_size`    - 各チャンクで処理される変数の数。
  * `channel_size`  - キュー内の未処理チャンクの最大数。

参照：[`mannwhitney!`](@ref)、[`mannwhitney`](@ref)
