現在のラジオデバイスのキャリア周波数を更新し、新しく取得したキャリア周波数でラジオオブジェクトを更新します。入力パラメータがUHDBindingオブジェクトの場合、希望するキャリア周波数はRxおよびTxの両方に適用されます。入力が[UHDRx]または[UHDTx]オブジェクトの場合、RxまたはTxのキャリア周波数のみが更新されます。

# –- 構文

updateCarrierFreq!(radio,carrierFreq)

# –- 入力パラメータ

  * radio	  : UHDデバイス [Union{UHDBinding,UHDRx,UHDTx}]
  * carrierFreq	: 新しい希望キャリア周波数
  * chan : 使用するチャネルインデックス（デフォルトは0）

# –- 出力パラメータ

  * 
