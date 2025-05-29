SDRからnbSamplesを受信し、出力バッファに格納します。バッファの形式はSDRバックエンドによって異なります。

# –– 構文

  * buffer = recv(radio, nbSamples)

# –– 入力パラメータ

  * radio : SDRオブジェクト
  * nbSamples : 希望するサンプル数

# –– 出力パラメータ

  * buffer : nbSamplesサンプルで満たされたラジオからの出力バッファ
