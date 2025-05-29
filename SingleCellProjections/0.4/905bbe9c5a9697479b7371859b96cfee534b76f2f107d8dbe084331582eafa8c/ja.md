```
merge_counts(samples, sample_names;
             lazy=false,
             sample_name_col = sample_names===nothing ? nothing : "sampleName",
             obs_id_col = "cell_id",
             obs_id_delim = '_',
             obs_id_prefixes = sample_names,
             extra_var_id_cols::Union{Nothing,String,Vector{String}},
             duplicate_var,
             duplicate_obs,
             callback=nothing)
```

`samples`をマージして1つの大きなDataMatrixを作成します。これは`obs`を連結することによって行われます。サンプルからの変数のユニオンが使用され、サンプルに変数が存在しない場合、そのカウントはゼロに設定されます。

`obs` IDは、現在の`obs` ID列を連結し、提供されている場合は`sample_names`と一緒に作成されます。

  * `lazy` - レイジーマージ。実際にマージを行うには`load_counts`を使用します。
  * `sample_name_col` - `sample_names`が格納されている列。
  * `obs_id_col` - マージ後の`obs` ID列の名前。（古い列名を保持するにはnothingに設定します。）
  * `obs_id_delim` - `obs` IDをマージする際に使用される区切り文字。
  * `obs_id_prefixes` - 新しいIDを作成するために使用されるプレフィックス（サンプルごとに1つ）。古いIDを保持するにはnothingに設定します。デフォルトは`sample_names`です。
  * `extra_var_id_cols` - マージ中に変数IDが一意であることを保証するために使用される追加の列。すべてのサンプルにその列が存在する場合、デフォルトは"feature_type"です。複数の列を含めるために`Vector{String}`にすることができます。無効にするにはnothingに設定します。
  * `duplicate_var` - 重複するvar IDが見つかった場合の動作を決定するために`:ignore`、`:warn`または`:error`に設定します。
  * `duplicate_obs` - 重複するobs IDが見つかった場合の動作を決定するために`:ignore`、`:warn`または`:error`に設定します。
  * `callback` - 実験的なコールバック機能。コールバック関数はマージ中にサンプルの間で呼び出されます。読み込みを中止するには`true`を返し、続行するには`false`を返します。

参照: [`load_counts`](@ref)
