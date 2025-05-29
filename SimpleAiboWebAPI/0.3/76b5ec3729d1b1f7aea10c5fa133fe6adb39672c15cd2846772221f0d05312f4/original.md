```
askPlayBone(
  category="holdMouth";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

asks `play_bone`.

This method is equivalent to `askAction("play_bone", Dict(Category=>holdMouth, Enqueue=>enqueue))`
