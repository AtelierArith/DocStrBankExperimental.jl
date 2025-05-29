```
LPCMFormat(channel_count::Int, sample_type::Type)
LPCMFormat(info::SamplesInfoV2)
```

OndaのデフォルトのインタリーブされたLPCMフォーマットに対応する`LPCMFormat<:AbstractLPCMFormat`インスタンスを返します。このフォーマットは、"lpcm"拡張子を持つサンプルデータファイルに対して想定されています。

`channel_count`は`length(info.channels)`に対応し、`sample_type`は`sample_type(info)`に対応します。

このフォーマットに対して（デ）シリアライズされたバイトはリトルエンディアンであることに注意してください（Onda仕様に従います）。
