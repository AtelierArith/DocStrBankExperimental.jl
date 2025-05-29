```
inputBasicParameters(;frequency::FT = 1e8, ieT::Symbol = :EFIE, CFIEα::FT = 0.6,
meshfilename::String = SimulationParams.meshfilename) where {FT<:AbstractFloat}
```

入力周波数パラメータ `frequency`、他のシミュレーションパラメータを変更する関数； 積分方程式タイプパラメータ `ieT`、計算プロセスで使用される積分方程式を変更； CFIE混合係数 `CFIEα`、メッシュファイル名 `meshfilename`。
