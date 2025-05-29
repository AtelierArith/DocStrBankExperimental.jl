```
from(name::String)::Supervised
```

Return the supervised node identified by full `name`.

Given for example the process `mytask` supervised by `mysupervisor`:

```
supervisor("mysupervisor", [process(mytask)])
```

then the full name of `mytask` process is `mysupervisor.mytask`.
