```
load_uvfits_and_array(uvfile, arrayfile=nothing; kwargs...)
```

eht-imagingを使用してuvfitsファイルを読み込み、eht-imagingの`Obsdata`オブジェクトを返します。オプションで、arrayfileとして配列ファイルを渡すこともでき、これによりテレスコープのフィールド回転情報などの追加情報が読み込まれます。これはeht-imagingによって生成された配列またはアンテナファイルであることが期待されます。
