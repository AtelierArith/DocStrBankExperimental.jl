ラジオのコアパラメータをTxまたはRxモードで初期化し、RFパラメータを開始します。

# –- 構文

openUHD(mode,sysImage,carrierFreq,samplingRate,txGain,antenna="RX2")

# –- 入力パラメータ

  * mode 			: "Tx"（送信機）または"Rx"（受信）モードでラジオを開くための文字列
  * carrierFreq	: 希望するキャリア周波数 [Union{Int,Float64}]
  * samplingRate	: 希望する帯域幅 [Union{Int,Float64}]
  * gain		: 希望するゲイン [Union{Int,Float64}]
  * antenna		: 希望するアンテナエイリアス Dict{Symbol,Vector[String]}（例：Dict(:Rx=>["RX2"],:Tx=>["TRX"]））

キーワード=

  * args	  : 追加のロードパラメータを含む文字列（例えば、FPHGAイメージへのパス） [String]

# –- 出力パラメータ

  * uhd		  	: UHDオブジェクト [UHDBinding]
