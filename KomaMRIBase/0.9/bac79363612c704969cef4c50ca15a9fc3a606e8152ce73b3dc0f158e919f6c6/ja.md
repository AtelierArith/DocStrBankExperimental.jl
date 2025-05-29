```
Mk, Mk_adc = get_Mk(seq::Sequence, k; Δt=1, skip_rf=zeros(Bool, sum(is_RF_on.(seq))))
```

シーケンス `seq` の $k$次モーメントを、$\int_0^T t^k G(t) dt$ の式に従って計算します。

# 引数

  * `seq`: (`::Sequence`) シーケンス構造体
  * `k`: (`::Integer`) 計算するモーメントの次数
  * `Δt`: (`::Real`, `=1`, `[s]`) ADC取得および勾配のための2つの時間サンプル間の名目上のデルタ時間間隔
  * `skip_rf`: (`::Vector{Bool}`, `=zeros(Bool, sum(is_RF_on.(seq)))`) 誘発または再焦点RFタイプのための積分をリセットする計算をスキップするかどうかを示すブールベクトル

# 戻り値

  * `Mk`: (`3-column ::Matrix{Real}`) $k$次モーメント
  * `Mk_adc`: (`3-column ::Matrix{Real}`) ADC時刻でサンプリングされた$k$次モーメント
