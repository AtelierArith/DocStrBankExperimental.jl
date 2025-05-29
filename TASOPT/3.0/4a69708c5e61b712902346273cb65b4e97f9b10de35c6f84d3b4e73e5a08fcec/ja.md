```
save_aircraft_model(ac::TASOPT.aircraft=TASOPT.read_aircraft_model(), 
datafile=joinpath(TASOPT.__TASOPTroot__, "IO/default_output.toml"),
save_output::Bool=false)
```

航空機モデルを辞書に変換し、それをTOMLファイルに書き込みます。書き込まれる値は、default_input.tomlに従って明示的に設定されます。すべての値はSI単位で書き込まれます。

この保存操作は、パラメータの繰り返しに関して追加の仮定を行います。具体的には、次の項目についてはすべての飛行セグメント/ポイントに同じ値が適用されます：     - parm[] パラメータ     - excrescence*drag*factors、翼のオーバースピード、翼/スタビライザーのRe_refs すべてのミッションおよび飛行セグメントに対しては、次の項目について同じ値が適用されます：     - parg[] および pare[] パラメータ     - 燃料温度

その値は、対応する配列軸の最初のエントリですが、他のポイントがより関連性のある一部の空力パラメータについては例外です（例："Cruise" "Takeoff"）。

*および変更可能

!!! note "デフォルトからの逸脱"
    デフォルトの機能から大きく逸脱するモデルについては、`read_input.jl`および`save_model.jl`の拡張が推奨されます。モデルに関する十分な知識が必要です。

