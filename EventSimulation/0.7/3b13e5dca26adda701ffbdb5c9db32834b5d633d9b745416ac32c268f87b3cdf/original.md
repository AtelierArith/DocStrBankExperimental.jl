Subtype of `Real` defining a lexicographically comparable pair of `Real`. It is designed to be used by `Scheduler` where standard real numbers run to a problem of undefined order of undefined order of removal from priority queue.

`PriorityTime` two fields `time` and `priority` may have different types, but both have to be subtypes of `Real`. `priority` should be used to determine order of execution of `Action`s that have the same time. Two actions with identical `time` and `priority` have undefined oreder of execution so this should be avoided.

`PriorityTime` type has defined lexicographic order and `+`, `-`. It is immutable, has a custom `hash` function and conversions from `Real` types.
