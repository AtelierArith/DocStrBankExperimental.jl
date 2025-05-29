現在のラジオデバイスのサンプリングレートを更新し、新しく取得したサンプリング周波数でラジオオブジェクトを更新します。入力パラメータがUHDBindingオブジェクトの場合、希望するサンプリング周波数はRxおよびTxの両方に適用されます。入力が[UHDRx]または[UHDTx]オブジェクトの場合、RxまたはTxのサンプリング周波数のみが更新されます。

# –- 構文

updateSamplingRate!(radio,samplingRate,chan=0)

# –- 入力パラメータ

  * radio	  : UHDデバイス [Union{UHDBinding,UHDRx,UHDTx}]
  * samplingRate	: 新しい希望サンプリングレート
  * chan : 使用するチャネルインデックス（デフォルトは0）

# –- 出力パラメータ

  * 
