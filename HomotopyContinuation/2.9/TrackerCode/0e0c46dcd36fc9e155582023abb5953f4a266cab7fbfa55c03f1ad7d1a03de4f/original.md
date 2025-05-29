```
TrackerCode
```

The possible states a `CoreTracker` can have are of type `TrackerCode.codes` and can be

  * `TrackerCode.success`: Indicates a successfull tracking.
  * `TrackerCode.tracking`: The tracking is still in progress.
  * `TrackerCode.terminated_accuracy_limit`: Tracking terminaed since the accuracy was insufficient.
  * `TrackerCode.terminated_invalid_startvalue`: Tracking terminated since the provided start value was invalid.
  * `TrackerCode.terminated_ill_conditioned`: Tracking terminated since the path was too ill-conditioned.
  * `TrackerCode.terminated_max_steps`: Tracking terminated since maximal number of steps is reached.
  * `TrackerCode.terminated_step_size_too_small`: Trackint terminated since the step size was too small.
  * `TrackerCode.terminated_unknown`: An unintended error occured. Please consider reporting an issue.
