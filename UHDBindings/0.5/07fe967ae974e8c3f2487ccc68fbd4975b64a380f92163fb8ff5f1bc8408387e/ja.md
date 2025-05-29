ラジオデバイスを通じてバッファを送信します。サイクリックパラメータをtrueに設定することで、サイクリックバッファ送信を強制することができます（ラジオは同じバッファを中断なく送信します）。

# –– 構文

send(radio,buffer,cyclic=false)

# –– 入力パラメータ

  * radio	  	: UHDデバイス [UHDRx]
  * buffer 	: 送信するバッファ [Union{Array{Complex{Cfloat}},Array{Cfloat}}]
  * cyclic 	: 同じバッファを複数回送信する（デフォルトはfalse） [Bool]

# –– 出力パラメータ

  * nbEch 	: 実際に送信されたサンプルの数 [Csize_t]。これは送信された複素サンプルの数に対応します。
