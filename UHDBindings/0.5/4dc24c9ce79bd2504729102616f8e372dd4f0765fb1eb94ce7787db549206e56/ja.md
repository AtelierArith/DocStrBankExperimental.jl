現在のラジオデバイスのゲインを更新し、新しく取得したゲインでラジオオブジェクトを更新します。入力パラメータがUHDBindingオブジェクトの場合、希望するゲインはRxおよびTxの両方に適用されます。入力が[UHDRx]または[UHDTx]オブジェクトの場合、RxまたはTxゲインのみが更新されます。

# –- 構文

updateGain!(radio,gain)

# –- 入力パラメータ

  * radio	  : UHDデバイス [Union{UHDBinding,UHDRx,UHDTx}]
  * gain	: 新しい希望ゲイン
  * chan : 使用するチャネルインデックス（デフォルトは0）

# –- 出力パラメータ

  * 
