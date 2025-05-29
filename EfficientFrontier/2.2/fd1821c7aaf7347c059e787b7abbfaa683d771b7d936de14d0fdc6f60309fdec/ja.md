```
   ECL!(aCL::Vector{sCL{T}}, PS::Problem{T}; numSettings = Settings(PS), incL=false, settings=SettingsQP(PS), settingsLP=SettingsLP(PS))  where T

すべてのクリティカルラインセグメントを計算します。Lが0に減少する場合（incL=trueの場合は+Infに増加します）、最初のセグメントはaCL[end]です。`settings`はLightenQPからの`LightenQP.Settings`設定です。戻り値：完了した場合はtrue
```
