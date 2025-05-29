```
askChangePosture(
  finalPosture="sit";
  enquee=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

は `change_posture` を要求します。

  * `finalPosture` は次の定数のいずれかである必要があります：

      * `back`
      * `crouch`
      * `down`
      * `down_and_lengthen_behind`
      * `down_and_shorten_behind`
      * `sit_and_raise__both_hands`
      * `sit`
      * `sleep`
      * `stand`
      * `stand_straight`

このメソッドは `askAction("change_posture", Dict(FinalPosture=>finalPosture, Enqueue=>enqueue))` と同等です。
