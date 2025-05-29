```
add_relay(data::Dict{String,Any}, element1::Union{String,SubString{String}}, element2::Union{String,SubString{String}}, id::Union{String,SubString{String}}, TS::Number, TDS::Number, CTs::Vector;
phase::Vector=[1,2,3], t_breaker::Number=0, kwargs...)
```

回路に差動リレーを追加する関数。正しく使用するためには、関心のある回路ファイルを編集し、対象の行をバスで分割する必要があります。そのバスに故障を追加できます。差を取るために、流入および流出電流を使用します。二次電流が定格の名目電流であると仮定して、電流変圧器の二次から制約曲線を計算します。Element1は流入、element2は流出です。入力:     必須         (1) data(Dictionary): .dssファイルのparse*file()関数から得られる辞書。         (2) element1(String): リレーが保護している最初の回路要素。         (3) element2(String): リレーが保護している第二の回路要素。リレーが正しく機能するためには、要素はそれぞれバスの間に故障がシミュレートされる同じラインの保護である必要があります。         (4) id(String): リレーID。         (5) trip*angle: 位相角の差が大きい場合にリレーがトリップする角度。

```
Optional
    (6) kwargs: ユーザーが望む追加の任意のもの。その他には使用されません。
```

出力:     差動リレーをデータ辞書に追加します。基本的に、.dssファイルで定義された回路に要素を追加します。
