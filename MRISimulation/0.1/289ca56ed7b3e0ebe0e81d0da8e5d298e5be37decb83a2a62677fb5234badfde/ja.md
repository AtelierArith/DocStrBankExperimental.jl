## 一般的なマルチエコーシーケンス（可変フリップ角およびTR）

励起パルスの位相は-90°であり、CPMG条件を満たすためです。

簡単のため、瞬時パルスが仮定されています。

エコーは、励起パルスの後、T*echo、2*T*echo、...、numContrasts*T_echoの時刻に現れます。

# フィールド

  * `excitationAngle::Float64`            - 励起パルスのフリップ角
  * `refocusingAngles :: Vector{Float64}` - 再焦点化パルスのフリップ角
  * `T_rf::Vector{Float64}`               - 励起パルスに対する再焦点化パルスの相対時間
  * `T_echo:: Vector{Float64}`            - 励起パルスに対するエコー時間
