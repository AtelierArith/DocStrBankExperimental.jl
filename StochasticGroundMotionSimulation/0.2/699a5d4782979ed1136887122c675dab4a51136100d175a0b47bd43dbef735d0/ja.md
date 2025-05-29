```
rms_duration(m::S, r_ps::T, src::SourceParameters, sdof::Oscillator, rvt::RandomVibrationParameters) where {T<:Real}
```

`rvt.dur_rms`に基づいて(Drms, Dex, Dratio)の3タプルを返します。デフォルトの`rvt`は、励振持続時間`Dex`に対して`:BT14`モデルを使用します。

  * `m`は大きさです
  * `r_ps`は等価点ソース距離です
