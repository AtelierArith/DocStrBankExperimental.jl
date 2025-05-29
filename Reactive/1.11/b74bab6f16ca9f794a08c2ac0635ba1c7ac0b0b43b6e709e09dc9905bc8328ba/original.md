```
merge(inputs...)
```

Merge many signals into one. Returns a signal which updates when any of the inputs update. If many signals update at the same time, the value of the *youngest* (most recently created) input signal is taken.
