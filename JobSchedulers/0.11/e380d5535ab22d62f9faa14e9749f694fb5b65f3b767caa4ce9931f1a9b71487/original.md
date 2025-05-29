```
ispast(j::Job) :: Bool = j.state === DONE || j.state === CANCELLED || j.state === FAILED
```
