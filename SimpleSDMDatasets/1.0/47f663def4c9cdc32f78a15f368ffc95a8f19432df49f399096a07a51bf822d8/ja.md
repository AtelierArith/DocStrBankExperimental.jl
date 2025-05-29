```
RasterData{P <: RasterProvider, D <: RasterDataset}
```

`RasterData`型は`SimpleSDMDatasets`の主なユーザー向け型です。具体的には、これは*シングルトン*のパラメトリック型であり、2つのパラメータは`RasterProvider`と`RasterDataset`の型です。内部コンストラクタは、プロバイダー/データセットのペアに対して`provides`メソッドを呼び出し、この組み合わせが存在するかどうかを確認します。
