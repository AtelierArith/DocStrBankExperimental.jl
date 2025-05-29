```
Hashpipe Status struct
```

Data representing a Hashpipe status buffer.

Need to create empty status struct before trying to attaching to existing status buffer. Example: '''     instance*id = 0     status = status*t(0,0,0,0)     status*attach(instance*id, Ref(status)) '''
