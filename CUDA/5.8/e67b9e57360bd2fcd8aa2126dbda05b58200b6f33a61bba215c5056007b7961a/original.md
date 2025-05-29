```
@assert cond [text]
```

Signal assertion failure to the CUDA driver if `cond` is `false`. Preferred syntax for writing assertions, mimicking `Base.@assert`. Message `text` is optionally displayed upon assertion failure.

!!! warning
    A failed assertion will crash the GPU, so use sparingly as a debugging tool. Furthermore, the assertion might be disabled at various optimization levels, and thus should not cause any side-effects.

