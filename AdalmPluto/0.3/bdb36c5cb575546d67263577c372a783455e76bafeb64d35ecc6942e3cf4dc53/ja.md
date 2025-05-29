```
openPluto(carrierFreq, samplingRate, bandwidth[, uri, backend])
```

PlutoSDR構造体を作成し、ラジオを構成してサンプルをストリーミングします。

# 引数

  * `carrierFreq::Int` : txおよびrxのキャリア周波数。
  * `samplingRate::Int` : txおよびrxのサンプリングレート。
  * `gain::Int` : アナログRXゲイン。

# キーワード

  * `addr::String="auto"` : ラジオアドレス（例: "usb:1.3.5"）。"auto"は指定されたバックエンドの最初に見つかったuriを使用します。
  * `backend::Union{nothing,String}` : 自動uriをスキャンするためのバックエンド。指定されていない場合、すべてのバックエンドがスキャンされ、最初に見つかったラジオが使用されます。
  * `bufferSize::UInt=1024*1024` : サンプルのバッファサイズ。
  * `bandwidth::Int` : txおよびrxの帯域幅。

# 戻り値

  * `radio::PlutoSDR` : 完全に初期化されたPlutoSDR構造体。
