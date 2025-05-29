USRPデバイスから単一のバッファを取得し、Buffer構造体を使用します。

# –– 構文

recv!(sig,radio,nbSamples)

# –– 入力パラメータ

  * sig	  : 構成する複素信号 [Array{Complex{Cfloat}}]
  * radio	  : UHDオブジェクト [UHDRx]
  * buffer  : バッファオブジェクト（setBuffer(radio)で取得） [Buffer]

# –– 出力パラメータ

  * 
