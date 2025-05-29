```
quicksave_aircraft(ac::TASOPT.aircraft=TASOPT.read_aircraft_model(),
    filepath=joinpath(TASOPT.__TASOPTroot__, "IO/default_quicksave_aircraft.jld2"))
```

航空機 `struct` を JLD2 を使用して .jld2 にシリアライズして保存します（人間が読める形式ではありません）。航空機モデルのすべてのフィールドを保存することを目的としています（すべてが save*aircraft*model によって保存されるわけではありません）。

!!! details "🔃 入力と出力"
    **入力:**

      * `ac::TASOPT.aircraft`: 任意の状態のモデルを含む TASOPT 航空機 `struct`。
      * `filepath::String`: 書き込む .jld2 ファイルのパスと名前。

    **出力:**

      * なし。

