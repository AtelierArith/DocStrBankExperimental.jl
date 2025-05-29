```
add_relay(data::Dict{String,Any}, element::String, id::String, TS::Number, TDS::Number;
phase::Vector=[1,2,3],t_breaker::Number=0, shots::Int=1, kwargs...)
```

指定された要素にCTなしの過電流リレーを各希望の相に追加する関数。呼び出し方: add*relay(ciruit*dictionary, "circuit*element", "name", TS(アンペア), TDS;         kwargs(format:t*c=1.0))

入力:     必須(5)         (1) data(Dictionary): .dssファイルのparse*file()関数からの辞書。         (2) element(String): リレーが保護/接続している回路要素。         (3) id(String): 同じゾーンに複数のリレーがある場合のリレーID（プライマリ、セカンダリなど）         (4) TS(Float): リレーのタップ設定。（CTを含めない）         (5) TDS(Float): タイムダイヤル設定     オプション         (6) phase(Vector): オプション。リレーが接続/保護している相。デフォルトは3相:[1,2,3](7) t*breaker(Number): オプション。ブレーカーの動作時間。         (8) Shots(Int): オプション。ロックアウト前の動作回数。         (9) kwargs: ユーザーが望む追加のもの。その他には使用されない。

出力:     データ辞書にリレーを追加します。基本的に、.dssファイルで定義された回路に要素を追加します。
