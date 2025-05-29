```
askPlayDice(
  category="holdMouthDice";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `change_posture`.

  * `category` should be one of the following constants:

      * `holdMouthDice`
      * `rollDiceLeft`
      * `rollDiceRight`
      * `rollDicePush`
      * `rollDicePull`
      * `stackDice`

This method is equivalent to `askAction("play_dice", Dict(Category=>category, Enqueue=>enqueue))`
