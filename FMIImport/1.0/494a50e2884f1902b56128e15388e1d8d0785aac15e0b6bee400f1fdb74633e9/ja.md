```
fmi3GetNumberOfContinuousStates(c::FMU3Instance)
```

この関数は連続状態の数を返します。この関数はモデル交換でのみ呼び出すことができます。

`fmi3GetNumberOfContinuousStates`は、構造パラメータが変更された後に呼び出す必要があります。構造パラメータが変更されていない限り、状態の数はmodelDescription.xmlに記載されており、この関数を呼び出す必要はありません。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 3.0標準のFMUのインスタンス化されたインスタンスを表します。

# 戻り値

  * `size::Integer`: 戻り値`size`は、このインスタンスの連続状態の数です。

# ソース

  * FMISpec3.0リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存定義
  * FMISpec3.0: 2.3.2. 状態: インスタンス化された

関連情報として[`fmi3GetNumberOfContinuousStates`](@ref)も参照してください。
