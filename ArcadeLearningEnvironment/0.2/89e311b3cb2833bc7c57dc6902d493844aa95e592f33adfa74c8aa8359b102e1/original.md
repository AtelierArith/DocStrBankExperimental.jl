```
act(ale_instance::ALEPtr, action::Integer)
```

Applies an action to the game and returns the reward. It is the user's responsibility to check if the game has ended and reset when neccessary - this function will keep pushing buttons on the game over screen.
