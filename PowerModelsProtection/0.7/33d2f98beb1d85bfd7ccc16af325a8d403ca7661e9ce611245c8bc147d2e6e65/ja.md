```
add_relay(data::Dict{String,Any}, element1::String, element2::String, id::String, trip_angle::Number;
kwargs...)
```

回路に方向性差動リレーを追加する関数。正しく使用するためには、関心のある回路ファイルを編集し、対象のラインをバスで分割する必要があります。そのバスに故障を追加できます。両端の電流と電圧の位相角を使用して、電力の方向が両端で同じかどうかを判断します。element1は出発点、element2は到達点です。入力:     必須         (1) data(Dictionary): .dssファイルのparse*file()関数から得られる辞書。         (2) element1(String): リレーが保護している最初の回路要素。         (3) element2(String): リレーが保護している2番目の回路要素。リレーが正しく機能するためには、要素はそれぞれ同じラインの保護であり、その間に故障がシミュレートされるバスが必要です。         (4) id(String): リレーID。         (5) trip*angle: 位相角の差が大きい場合にリレーがトリップする角度。

```
Optional
    (6) kwargs: ユーザーが望む追加の任意のもの。その他には使用されません。
```

出力:     差動リレーをデータ辞書に追加します。基本的に、.dssファイルで定義された回路に要素を追加します。
