```
latex_unit(id::String;
           paren::Bool = true,
           squared::Bool = false,
           space::Bool = true,
           unicode::Bool = false
)
```

単位を返します。与えられたもの：

  * `id` 単位の識別子（ライブラリにない場合は、idを単位として使用）
  * `paren` オプション：trueの場合、括弧を含める
  * `squared` オプション：trueの場合、`[]`を使用し、そうでない場合は`()`を使用
  * `space` オプション：trueの場合、先頭にスペースを追加
  * `unicode` オプション。trueの場合、ユニコードを返し、そうでない場合はアップグリーク文字列を返す

定義済みの単位には以下が含まれます：

  * `A` μmol CO₂ m⁻² s⁻¹
  * `E` mol H₂O m⁻² s⁻¹
  * `E_MMOL` mmol H₂O m⁻² s⁻¹
  * `G` mol m⁻² s⁻¹
  * `PAR` μmol m⁻² s⁻¹
  * `T` °C
  * `WUE` μmol mol⁻¹
