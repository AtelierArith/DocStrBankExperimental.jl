```
askPlayDice(
  category="holdMouthDice";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

は `change_posture` を要求します。

  * `category` は次の定数のいずれかである必要があります：

      * `holdMouthDice`
      * `rollDiceLeft`
      * `rollDiceRight`
      * `rollDicePush`
      * `rollDicePull`
      * `stackDice`

このメソッドは `askAction("play_dice", Dict(Category=>category, Enqueue=>enqueue))` と同等です。
