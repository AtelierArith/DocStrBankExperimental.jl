LoRaシンボルを生成する sig,bitSeq,bitEnc,bitInter = loraEncode(N,SF,BW,Fs,inverse)

# 入力

  * N: 送信するブロックの数、ブロックはSF LoRaシンボルに対応
  * SF: CSS変調のスプレッディングファクター
  * BW: 送信に使用される帯域幅
  * Fs: サンプリング周波数
  * inverse: 0はアップチャープを送信、1はダウンチャープを送信

# 出力

  * sig : 送信機から放出されるベースバンド信号（複素形式）
  * bitSeq : ランダムに生成されたバイナリデータ（ペイロードメッセージ）
  * bitEnc : ハミング符号化後のバイナリシーケンス
  * bitInterl : インタリーブ後のバイナリシーケンス

ディスパッチメソッド :  sig,bitSeq,bitEnc,bitInter = lora_encode(bitSeq,SF,BW,Fs,inverse) 

  * ペイロードメッセージbitSeqを使用（サイズはN x SF x 4でなければならない）
