```
Samples(data::AbstractMatrix, info::SamplesInfoV2, encoded::Bool;
        validate::Bool=Onda.VALIDATE_SAMPLES_DEFAULT[])
```

次のフィールドを持つ `Samples` インスタンスを返します：

  * `data::AbstractMatrix`: サンプルデータの行列。行列の `i` 行目は `info.channels` の `i` チャンネルに対応し、`j` 列目は `j` 番目のマルチチャネルサンプルに対応します。
  * `info::SamplesInfoV2`: `Samples` インスタンスを説明する [`SamplesInfoV2`](@ref) 準拠の値。
  * `encoded::Bool`: `true` の場合、`data` の値は `Samples` インスタンスの `info` に従って LPCM エンコードされています。`false` の場合、`data` の値は `info` の標準単位にデコードされています。

`validate` が `true` の場合、構築された `Samples` インスタンスに対して [`Onda.validate_samples`](@ref) が呼び出され、返される前に検証されます。

`getindex` と `view` は `Samples` に対して通常の整数インデックスを受け入れるように定義されていますが、行インデックスにはチャンネル名やチャンネル名に一致する正規表現を、列インデックスには `TimeSpan` 値を受け入れます。詳細なインデックスの例については `Onda/examples/tour.jl` を参照してください。

また、`getindex(s, ...)` を介して `s::Samples` からコピーされた「スライス」は、過剰なオーバーヘッドを避けるために `s.info` をエイリアスする場合があります。これは、一般的に `s.info`、特に `s.info.channels` を直接変更することを避けるべきであることを意味します。

参照： [`load`](@ref), [`store`](@ref), [`encode`](@ref), [`encode!`](@ref), [`decode`](@ref), [`decode!`](@ref)
