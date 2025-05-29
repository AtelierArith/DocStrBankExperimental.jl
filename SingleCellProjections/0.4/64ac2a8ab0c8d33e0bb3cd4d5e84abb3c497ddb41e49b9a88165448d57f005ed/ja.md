```
load_counts([loadfun=load10x], filenames;
            sample_names,
            sample_name_col,
            obs_id_col = "cell_id",
            lazy,
            lazy_merge = false,
            obs_id_delim = '_',
            obs_id_prefixes = sample_names,
            extra_var_id_cols::Union{Nothing,String,Vector{String}},
            duplicate_var,
            duplicate_obs,
            callback=nothing)
```

複数のサンプルを効率的に読み込み、マージします。

デフォルトでは、10x CellRangerファイルを読み込みます。ファイルは最初に遅延読み込みされ、その後マージされたカウント行列が割り当てられ、最後に各サンプルが直接マージされたカウント行列に読み込まれます。（この戦略は、データのコピーが2つではなく1つだけ必要なため、メモリ使用量を大幅に削減します。）

`filenames`は、どのファイルを読み込むかを指定します。（ファイル名のベクターまたは単一のファイル名文字列であることができます。）各ファイルに対して、`loadfun`が呼び出されます。

  * `sample_names` - サンプル名を指定します。`filenames`と同じ長さのベクターである必要があります。サンプル名の注釈を作成しないには`nothing`に設定します。
  * `sample_name_col` - `obs`内のサンプル名の列、デフォルトは"sampleName"です。
  * `obs_id_col` - `obs`内のマージされた`id`の列です。
  * `lazy` - 遅延読み込みを有効にします。`load10x`が使用されている場合はデフォルトでtrue、そうでない場合はfalseです。
  * `lazy_merge` - 遅延マージを有効にします。つまり、`var`と`obs`は作成されますが、カウント行列のマージは`load_counts`への2回目の呼び出しまで延期されます。
  * `obs_id_delim` - マージされた`obs` IDを作成する際に使用される区切り文字です。
  * `obs_id_prefixes` - 新しいIDを作成するために使用されるプレフィックス（サンプルごとに1つ）。古いIDを保持するには何も設定しないでください。デフォルトは`sample_names`です。
  * `extra_var_id_cols` - マージ中に変数IDが一意であることを保証するために使用する追加の列です。すべてのサンプルにその列が存在する場合、デフォルトは"feature_type"です。複数の列を含めるために`Vector{String}`にすることができます。無効にするには何も設定しないでください。
  * `duplicate_var` - 重複する変数IDが見つかった場合の動作を決定するために`:ignore`、`:warn`または`:error`に設定します。
  * `duplicate_obs` - 重複する観測IDが見つかった場合の動作を決定するために`:ignore`、`:warn`または`:error`に設定します。
  * `callback` - 実験的なコールバック機能。コールバック関数はマージ中にサンプル間で呼び出されます。読み込みを中止するには`true`を返し、続行するには`false`を返します。
  * 追加のkwargs（指定された場合の`duplicate_var`/`duplicate_obs`を含む）は`loadfun`に渡されます。

# 例

サンプルを読み込み、名前を付けます：

```julia
julia> counts = load_counts(["s1.h5", "s2.h5"]; sample_names=["Sample A", "Sample B"])
```

関連情報: [`load10x`](@ref), [`merge_counts`](@ref)
