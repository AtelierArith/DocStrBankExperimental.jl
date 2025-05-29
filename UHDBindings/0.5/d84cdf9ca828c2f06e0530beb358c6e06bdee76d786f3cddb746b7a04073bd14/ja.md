USRPデバイスから単一のバッファを取得し、必要なリソースをすべて作成します。

# –– 構文

sig	  = recv(radio,nbSamples)

# –– 入力パラメータ

  * radio	  : UHDオブジェクト [UHDRx]
  * nbSamples : 希望するサンプル数 [Int]

# –– 出力パラメータ

  * sig	  : ラジオからのベースバンド信号 [Array{Complex{CFloat}},radio.packetSize]
