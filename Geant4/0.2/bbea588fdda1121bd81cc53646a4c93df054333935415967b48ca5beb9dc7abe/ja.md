```
G4JLSensitiveDetector(name::String, data::DATA; <keyword arguments>) where DATA<:G4JLSDData
```

G4JLSensitiveDetectorをその名前と関連するDATA構造体で初期化します。

# 引数

  * `name::String`: センシティブ検出器の名前
  * `data::DATA`: センシティブ検出器に関連するデータ構造
  * `processhits_method=nothing`: シグネチャを持つprocessHit関数: `(data::DATA, step::G4Step, ::G4TouchableHistory)::Bool`
  * `initialize_method=nothing`: シグネチャを持つ初期化関数: `(data::DATA, ::G4HCofThisEvent)::Nothing`
  * `endofevent_method=nothing`: シグネチャを持つendOfEvent関数: `(data::DATA, ::G4HCofThisEvent)::Nothing`
