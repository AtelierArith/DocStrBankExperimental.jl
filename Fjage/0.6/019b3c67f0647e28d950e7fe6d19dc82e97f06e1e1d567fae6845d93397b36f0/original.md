```
delay(b::CoroutineBehavior, millis)
```

Block the behavior for `millis` milliseconds.

Unlike `block()`, this function blocks immediately and only resumes once the block has expired. Unlike `Base.sleep()`, this function releases the lock on the behavior's agent.
