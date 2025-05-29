```
fmi3GetNumberOfEventIndicators(c::FMU3Instance)
```

この関数はイベントインジケーターの数を返します。この関数はモデル交換の中でのみ呼び出すことができます。

`fmi3GetNumberOfEventIndicators`は、構造パラメータが変更された後に呼び出す必要があります。構造パラメータが変更されていない限り、状態の数はmodelDescription.xmlに記載されており、この関数を呼び出す必要はありません。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表します。

# 戻り値

  * `size::Integer`: 戻り値`size`はこのインスタンスのイベントインジケーターの数です。

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存定義
  * FMISpec3.0: 2.3.2. 状態: インスタンス化された

他にも[`fmi3GetNumberOfEventIndicators`](@ref)を参照してください。
