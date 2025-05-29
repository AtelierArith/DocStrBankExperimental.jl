```
abstract type Callback end
```

Abstract type to trigger callbacks after some number of insertions. SearchGraph stores the callbacks in `callbacks` (a dictionary that associates symbols and callback objects); A SearchGraph object controls when callbacks are fired using `callback_logbase` and `callback_starting`
