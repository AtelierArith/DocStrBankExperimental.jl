UHD関数ラッパーを呼び出してバッファを埋める。recvまたはrecv!を使用してこの関数を呼び出すことが望ましい。

# –- 構文

recv!(sig,radio,nbSamples)

# –- 入力パラメータ

  * radio	  	: UHDオブジェクト [UHDRx]
  * ptr  		: 書き込み可能なメモリ位置 [Ref{Ptr{Cvoid}}]
  * nbSamples : 取得するサンプルの数

# –- 出力パラメータ

  * nbSamp 	: バッファに埋め込まれたサンプルの数 [Csize_t]
