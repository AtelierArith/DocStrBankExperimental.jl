ソフトウェア定義ラジオをバックエンドの'type'で開き、入力パラメータに基づいて調整し、サポートされているキーワードを使用します。これは、使用できるSDRのタイプに応じて、すべてのAbstractSDRがサポートする関数で使用できるラジオオブジェクトを返します。

# –- 構文

radio = openSDR(type,carrierFreq,samplingRate,gain,antenna;key)

# –- 入力パラメータ

  * type  : 希望するSDRタイプ。サポートされている異なるラジオフォーマットはgetSupportedSDR()で取得できます。
  * carrierFreq : キャリア周波数 [Hz]
  * samplingRate : サンプリング周波数 (Hz)
  * gain : アナログ受信ゲイン (dB)

# –- 出力パラメータ

  * radio : 定義されたSDRオブジェクト
