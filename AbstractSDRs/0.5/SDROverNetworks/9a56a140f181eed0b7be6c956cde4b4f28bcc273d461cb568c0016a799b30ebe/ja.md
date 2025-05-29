UHDネットワークリモートデバイスを開き、ソケットを初期化する –– 構文

openUhdOverNetwork(carrierFreq,samplingRate,gain,antenna="RX2";ip="192.168.10.11")

# –– 入力パラメータ

  * carrierFreq	: 希望するキャリア周波数 [Union{Int,Float64}]
  * samplingRate	: 希望する帯域幅 [Union{Int,Float64}]
  * gain		: 希望する受信ゲイン [Union{Int,Float64}]

キーワード 

  * ip	  : uhdOverNetwork IPアドレス
  * antenna		: 希望するアンテナエイリアス (デフォルト "TX-RX") [String]

# –– 出力パラメータ

  * structuhdOverNetwork    : uhdOverNetworkパラメータを持つ構造体 [SDROverNetwork]
