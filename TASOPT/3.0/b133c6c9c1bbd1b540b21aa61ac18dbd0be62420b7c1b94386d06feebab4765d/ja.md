```
quickload_aircraft(datafile=joinpath(TASOPT.__TASOPTroot__, "IO/default_quicksave_aircraft.jld2"))
```

`quicksave_aircraft()`によって生成された.jld2ファイルを読み込み、生成された`aircraft`構造体を返します。

!!! details "🔃 入力と出力"
    **入力:**

      * `filepath::String`: 書き込む.jld2ファイルのパスと名前。

    **出力:**

      * `ac::TASOPT.aircraft`: 保存された状態のモデルを持つTASOPT航空機`struct`。

