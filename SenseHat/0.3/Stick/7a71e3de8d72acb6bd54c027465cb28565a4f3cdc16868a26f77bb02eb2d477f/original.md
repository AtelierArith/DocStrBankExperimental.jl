```
StickEvent(timestamp::DateTime, direc::Direc, state::State)
```

The data from a joystick event. The type contains the following fields:

  * `timestamp` : `DateTime` of when the event occurred.
  * `direc` : the direcion of the event, either `UP`, `DOWN`, `LEFT`, `RIGHT`, `MIDDLE` (`MIDDLE` occurs when the button is pressed down).
  * `state` : the state of the event (`PRESS`, `RELEASE`, `HOLD`).
