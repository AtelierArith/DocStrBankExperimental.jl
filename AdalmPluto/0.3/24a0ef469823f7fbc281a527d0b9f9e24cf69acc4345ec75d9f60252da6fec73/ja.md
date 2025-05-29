```
openPluto(txCfg, rxCfg[, uri, backend])
```

PlutoSDR構造体を作成し、サンプルをストリーミングするようにラジオを構成します。

# 引数

  * `txCfg::ChannelCfg` : txチャネルのポート / 帯域幅 / サンプリングレート / キャリア周波数。
  * `rxCfg::ChannelCfg` : rxチャネルのポート / 帯域幅 / サンプリングレート / キャリア周波数。
  * `bufferSize::UInt=1024*1024` : サンプルのバッファサイズ。
  * `uri::String="auto"` : ラジオのuri（例： "usb:1.3.5"）。 "auto"は、指定されたバックエンドに対して見つかった最初のuriを取得します。
  * `backend::Union{nothing,String}` : 自動uriをスキャンするためのバックエンド。指定されていない場合、すべてのバックエンドがスキャンされ、見つかった最初のラジオが使用されます。

# 戻り値

  * `radio::PlutoSDR` : 完全に初期化されたPlutoSDR構造体。
