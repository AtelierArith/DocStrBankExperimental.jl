```
load10x(filename; lazy=false, var_id=nothing, var_id_delim='_')
```

CellRangerの".h5"または".mtx[.gz]"ファイルをDataMatrixとして読み込みます。

  * `lazy` - `true`の場合、カウントマトリックス自体は読み込まれず、特徴とバーコードのみが読み込まれます。これは、サンプルをより効率的にマージするために`load_counts`内で内部的に使用されます。後でカウントデータを読み込むには`load_counts`を使用してください。
  * `var_id` - ペア`var_id_col=>cols`がある場合、列`cols`の内容がマージされて新しいIDが作成されます。IDが一意であることを保証するのに便利です。
  * `var_id_delim` - 変数列をマージして変数ID列を作成する際に使用される区切り文字。

# 例

CellRangerの".h5"ファイルからカウントを読み込みます。（推奨）

```julia
julia> counts = load10x("filtered_feature_bc_matrix.h5")
```

CellRangerの".mtx"ファイルからカウントを読み込みます。同じフォルダ内でバーコードと特徴の注釈ファイルを探します。

```julia
julia> counts = load10x("matrix.mtx.gz")
```

遅延読み込みの後に読み込みを行います。

```julia
julia> counts = load10x("filtered_feature_bc_matrix.h5");
julia> counts = load_counts(counts)
```

参照: [`load_counts`](@ref) ```
