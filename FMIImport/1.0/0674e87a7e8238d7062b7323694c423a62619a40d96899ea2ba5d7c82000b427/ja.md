```
fmi3GetNumberOfEventIndicators!(c::FMU3Instance, nEventIndicators::Ref{Csize_t})
```

この関数はイベントインジケーターの数を返します。この関数はモデル交換でのみ呼び出すことができます。

`fmi3GetNumberOfEventIndicators`は、構造パラメータが変更された後に呼び出す必要があります。構造パラメータが変更されていない限り、状態の数はmodelDescription.xmlに記載されており、この関数を呼び出す必要はありません。

# 引数

  * `c::FMU3Instance`: FMI 3.0標準のFMUのインスタンス化されたインスタンスを表す可変構造体。
  * `nEventIndicators::Ref{Csize_t}`: 関数によって返される連続状態の数を格納します。

# 戻り値

  * `status::fmi3Status`: 戻り値`status`は`fmi3Status`型の列挙であり、関数呼び出しの成功を示します。

詳細:

  * `fmi3OK`: 問題なし
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.3.2. 状態: インスタンス化された

さらに[`fmi3GetNumberOfEventIndicators!`](@ref)を参照してください。
