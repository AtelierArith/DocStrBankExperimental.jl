```
askPlayMotion(
  category="agree";
  enqueue=false,
  mode="NONE",
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `play_motion`.

  * `category` should be one of the following constants. Optional `Mode` parameters other than "NONE" are also listed.

      * `agree`
      * `bad`
      * `bark`
      * `beckon`

          * `Mode`: `BODY_LEFT`
          * `Mode`: `BODY_RIGHT`
      * `belch`
      * `bentBack`
      * `breath`
      * `curious`
      * `dance`
      * `drawInOnesChin`
      * `dreaming`
      * `friendly`
      * `friendlyPolite`
      * `gasp`
      * `halfAsleep`
      * `handsUp`
      * `happyOrHot`
      * `heading`

          * `Mode`: `NONE`
          * `Mode`: `SPACE_LEFT`
          * `Mode`: `SPACE_RIGHT`
      * `helloIloveYou`
      * `highFive`

          * `Mode`: `NONE`
          * `Mode`: `BODY_LEFT`
          * `Mode`: `BODY_RIGHT`
      * `imFriendly`
      * `jiggle`
      * `kiss`
      * `lickBody`

          * `Mode`: `BODY_LEFT`
          * `Mode`: `BODY_RIGHT`
      * `lookAroundHead`
      * `lookOver`
      * `marking`

          * `Mode`: `BOY`
          * `Mode`: `GIRL`
      * `nodHead`
      * `openMouth`
      * `overJoyed`
      * `paw`

          * `Mode`: `BODY_LEFT`
          * `Mode`: `BODY_RIGHT`
      * `peace`

          * `Mode`: `SPACE_LEFT`
          * `Mode`: `SPACE_RIGHT`
      * `perceive`
      * `playBiting`
      * `prettyPlease`
      * `ready`
      * `relax`
      * `restless`
      * `rubBack`
      * `scratchFloor`
      * `scratchHead`

          * `Mode`: `HIND_LEFT`
          * `Mode`: `HIND_RIGHT`
      * `shakeHead`
      * `shakeHipsBehind`
      * `shudder`
      * `sideKick`

          * `Mode`: `FRONT_LEFT`
          * `Mode`: `FRONT_RIGHT`
      * `sideUp`

          * `Mode`: `BODY_LEFT`
          * `Mode`: `BODY_RIGHT`
      * `sing`
      * `sleepTalking`
      * `sneeze`
      * `sniff`
      * `sniffDown`
      * `sniffUp`
      * `startled`
      * `startledLittle`
      * `stretch`
      * `swing`
      * `touched`

          * `Mode`: `SPACE_CENTER`
      * `waiting`
      * `washFace`
      * `whine`
      * `wiggleEar`

          * `Mode` : `BODY_BOTH`
      * `woof`
      * `yap`
      * `yawn`

This method is equivalent to `askAction("play_motion", Dict(Category=>category, Mode=>mode, Enqueue=>enqueue))`
