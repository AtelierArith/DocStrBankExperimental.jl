```
askChangePosture(
  finalPosture="sit";
  enquee=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `change_posture`.

  * `finalPosture` should be one of the following constants:

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

This method is equivalent to `askAction("change_posture", Dict(FinalPosture=>finalPosture, Enqueue=>enqueue))`
